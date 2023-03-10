/* 

-- author: jkopacko  

  += Descriptive names: deviceTypePath  
  += Variable type: String -- Ex: \device_types\device_type_000006  
  += Value: wildcards are supported  
  += version 1.0 - 03/01/23  

KEY: device type "00000#"  

0 = optical drive  
1 = floppy drive  
2 = modem  
3 = encrypted storage  
4 = infrared  
5 = wireless  
6 = removeable storage  
7 = bluetooth  
8 = mtp  
*/

WITH policyTimeStamp AS (
SELECT name, (key || data || '$$deviceTypePath$$') AS policyPath, (key || data || '$$deviceTypePath$$' || '\exemptions\exemption_000%') AS fullPath, datetime(mtime, 'unixepoch', 'localtime') AS modifiedTimeStamp
FROM registry
WHERE key = 'HKEY_LOCAL_MACHINE\SOFTWARE\Sophos\Management\Policy\DeviceControl\'
AND name = 'latest'
),
policyTypeDefault AS (
SELECT name, data, datetime(mtime, 'unixepoch', 'localtime') AS modifiedTimeStamp
FROM registry
WHERE key = (SELECT policyPath FROM policyTimeStamp)),
exemptListAccess AS (
SELECT name, data, datetime(mtime, 'unixepoch', 'localtime') AS modifiedTimeStamp, key, path
FROM registry
WHERE key LIKE (SELECT fullPath FROM policyTimeStamp)
AND name = "access"),
exemptListDeviceID AS (
SELECT name, data, datetime(mtime, 'unixepoch', 'localtime') AS modifiedTimeStamp, key, path
FROM registry
WHERE key LIKE (SELECT fullPath FROM policyTimeStamp)
AND name = "device_id"),
exemptListInstanceID AS (
SELECT name, data, datetime(mtime, 'unixepoch', 'localtime') AS modifiedTimeStamp, key, path
FROM registry
WHERE key LIKE (SELECT fullPath FROM policyTimeStamp)
AND name = "instance_id"),
exemptListDeviceAccess AS (
SELECT exemptListAccess.data AS policyAction,
exemptListDeviceID.data AS peripheral,
exemptListDeviceID.modifiedTimeStamp
FROM exemptListAccess
JOIN exemptListDeviceID
ON exemptListAccess.key = exemptListDeviceID.key),
exemptListInstanceAccess AS (
SELECT exemptListAccess.data AS policyAction,
exemptListInstanceID.data AS peripheral,
exemptListInstanceID.modifiedTimeStamp
FROM exemptListAccess
JOIN exemptListInstanceID
ON exemptListAccess.key = exemptListInstanceID.key),
exemptMasterList AS (
SELECT *
FROM exemptListDeviceAccess
UNION ALL
SELECT *
FROM exemptListInstanceAccess)
SELECT DISTINCT * FROM exemptMasterList
