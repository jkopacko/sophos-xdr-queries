# Sophos Central XDR Queries

This repo hosts Live Discover Queries written for Sophos Central

## Read The Comments

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

If changes occur to Sophos Central XDR schema that causes a failure, I will do my best to stay on top of them, but reach out with the repo link and screen of the error described to notifications@kopacko.us.
  
### Disclaimer
  
The queries are not supported via Sophos Support Channels and are provided "as-is."
