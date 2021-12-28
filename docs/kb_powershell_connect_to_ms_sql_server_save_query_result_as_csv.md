---
title: PowerShell: Connect to MS SQL Server and save results as CSV
keywords: documentation
last_updated: October 19th, 2021
tags: [admin-guide]
sidebar: mydoc_sidebar
layout: doc

---

#### PowerShell: Connect to MS SQL Server and save results as CSV

The following is an example PowerShell script to connect to a Microsoft SQL Database and dump the results of a query into a CSV file.
You will need to change the connections variables at the top of the script along with the $OuputFile and your SQL query at $SqlQuery

```

# SQL Connection Variables - Change
$SQLServer = "SQLServerName.mydomain.local" 
$SQLDBName = "Database_Name"
$SQLUsername = "SQLReaderUser"
$SQLPassword = "MySQLPassword"
 
# Where to save the output CSV file - Change
$OuputFile = "c:\dump\my_export.csv"
 
# Your SQL Query - Change
$SqlQuery = "SELECT  
    rtrim(EmployeeNumber) as EmployeeNumber,
    rtrim(JobTitle) as JobTitle,
    rtrim(City) as City,
    rtrim(CostCentre) as CostCentre,
    rtrim(ManagerEmployeeNumber) as ManagerEmployeeNumber
  FROM [$SQLDBName].[dbo].[Employee_Basic]"
   
# Delete the output file if it already exists
If (Test-Path $OuputFile ){
    Remove-Item $OuputFile
}
  
Write-Host "INFO: Exporting data from $SQLDBName to $OuputFile" -foregroundcolor white -backgroundcolor blue
  
# Connect to SQL Server using non-SMO class 'System.Data': 
$SqlConnection = New-Object System.Data.SqlClient.SqlConnection 
$SqlConnection.ConnectionString = "Server = $SQLServer; Database = $SQLDBName; User ID = $SQLUsername; Password = $SQLPassword"
  
$SqlCmd = New-Object System.Data.SqlClient.SqlCommand 
$SqlCmd.CommandText = $SqlQuery
$SqlCmd.Connection = $SqlConnection
  
$SqlAdapter = New-Object System.Data.SqlClient.SqlDataAdapter 
$SqlAdapter.SelectCommand = $SqlCmd
  
$DataSet = New-Object System.Data.DataSet 
$SqlAdapter.Fill($DataSet) 
$SqlConnection.Close() 
 
#Output RESULTS to CSV
$DataSet.Tables[0] | select "EmployeeNumber","JobTitle","City","CostCentre","ManagerEmployeeNumber" | Export-Csv $OuputFile

```
