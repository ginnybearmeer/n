# Database Schema

This is a complete guide of the PCM data class.


## registered version

| marketplace ID | Version | Update Time |
| --- | ---| --- |
| PCM | 001 |



*****

## Table schema


### PCM_file

- Describe  : contaim basic information
- Table_id  : PCM_file						
 
| NAME | TYPE | NOT NULL | DESCRIPTION | REFERENCE | CHECK | 
|:---|:---|:---|:---|:---|:---|
|file_id:key: | string |`TRUE`| unique identifier to the testing record of each pcm report,auto-generation UUID format from the backend.Format: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx (32 hexadecimal characters and 4 hyphens) |  |  |
| file_name | string| `TRUE`|PCM report file name.<br>naming rule:<br>\[BIOS Version]\<scenario detail\>\_\<Code name>\_\<TDP>\_PCM_Report-<template verion\>\_\<Date>\_<Time\>.xlsx<br>Exapmle:<br>[001900]S0_Kraken14_15W_PCM_Report-2.0.0_20221122_223055.xlsx |  |  |
| data_source | string | `TRUE` | which method to deal with PCM report.<br>format:<br>starliner-web/ starliner-tool/ vcosmos ... |  |  |
| uploader | string | `TRUE` | mail format.|  |  |
| marketplace_id | string | `TRUE` | Starliner marketplace id |  |  |
| version | int | `TRUE` | PCM report version. |  |  |
| version | timestamp |  `TRUE`| file upload time. <br>Format:<br> YYYY-MM-DD hh:mm:ss |  |  |






### PCM_file

- Describe  : contaim basic information
- Table_id  : PCM_file						
 
| NAME | TYPE | NOT NULL | DESCRIPTION | REFERENCE | CHECK | 
|:---:|:---:|:---:|:---|:---:|:---:|
| file_id | string |`True`| unique identifier to the testing record of each pcm report, auto-generation UUID format from the backend. |  [[pcm_file].[file_id]](#PCM_file)|  |
| function | string |`True` |The corresponding function of each value|||
| HDD_supplier | string |`True`|The corresponding HDD Supplier information|||
| HDD_PN | string |`False`|  The corresponding HDD PN information |  |  |
| HDD_GB | int |`False`|  The corresponding HDD GB information (unit:GB) |  |  |



### Template

- Describe  : 
- Table_id  : 		
 
| Name | Type | Allow Null | Description | Referenced | Check Constraint | 
|:---:|:---:|:---:|:---|:---:|:---:|
| |  | |  | |  |
