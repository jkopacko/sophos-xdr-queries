# Sophos Central EDR/XDR Queries 
| UPDATED AUGUST 2024 |

This repo hosts EDR and XDR Queries written for Sophos Central. This is a collection amassing 3 years, so please test on a non-prod machine. Code fragments in the OLD FORMAT may need a revision on column name formatting changes that occurred in the platform data set.

## Read The Comments

[CURRENT FORMAT] 
/***********************
Description:
Source:     [Data Lake | Live Endpoint]  
OS:         [Windows | Mac | Linux]       
Variable:   [OPTIONAL]
  +NAME
  +TYPE
  +VALUE
************************/


[OLD FORMAT -- TEST FOR ACCURACY]
  += **Descriptive names**: <variableName>  
  += **Variable type**: <type>  
  += **Value**: <value>  
  += **Version** ## - MM/DD/YY  
  += **Query type**: <L/D or D/L>  
  += **OS Support**: <Windows, Linux, or macOS>  

**Variable type** is a menu drop down selection of String, Date, SHA-256, IP Address, sophosPID, URL. Registry Key, File Path, Device Name, Username. N/A indicates no type is required.
  
**Value** is determined by the variable type. Items like Date will give you a menu option, otherwise, you manually enter the value. You can use wildcards here (%). N/A indicates no type is required.
  
**Version** number and dates are kept to help maintain the integrity of the code. 

**Query type** indicates if it is Live Discover (on agent) or Data Lake (on Central cloud).
  
**OS Support** indicates the operating system the query is designed for. Data Lake queries will not have this value.
  
### Disclaimer
  
The queries are not supported via Sophos Support Channels and are provided "as-is."
