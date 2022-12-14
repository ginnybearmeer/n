# __HW-PCM__

![alt text](https://hp.sharepoint.com/teams/BPSEngineeringDigitization/_layouts/15/download.aspx?SourceUrl=%2Fteams%2FBPSEngineeringDigitization%2FShared%20Documents%2FProduct%20Owners%2FMVP%20Clarification%2FHW%2DPCM%2FPCM%5FProcssing%5FFlow%2Epng)

<br>

# __Database Schema__

> This is a complete guide to the PCM metadata structure information. A database file for generating by using [DB Browser for SQLite](https://sqlitebrowser.org/).


<br>

*****


## __📕 Table of Contents__
<br>

<!--ts-->
   * 📑 [Register](#📑-register)
   * 🔎 [Overview](#🔎-overview)
     * [Entity Relationship Diagram](#●-entity-relationship-diagram)
     * [Database Name](#●-database-name)
     * [Table Extract](#●-table-extract)<br>
        1 &emsp;[PCM_file](#1-pcm_file)<br>
        2 &emsp;[PCM_HDD](#2-pcm_hdd)<br>
        3 &emsp;[PCM_LCD](#3-pcm_lcd)<br>
        4 &emsp;[PCM_RAM](#4-pcm_ram)<br>
        5 &emsp;[PCM_platform_spec](#5-pcm_platform_spec)<br>
        6 &emsp;[PCM_platform_config](#6-pcm_platform_config)<br>
        7 &emsp;[PCM_config_data](#7-pcm_config_data)<br>
        8 &emsp;[PCM_raw_data](#8-pcm_raw_data)<br>
        9 &emsp;[PCM_raw_data_sheet](#9-pcm_raw_data_sheet)<br>
        10 &ensp;[PCM_app](#10-pcm_spp)<br>
        11 &ensp;[PCM_driver](#11-pcm_driver)
<br>

*****
##  __📑 Register__

- Version: PCM001 
- Pubulish time: 2022-12-07

<br>


<br>

---
## __🔎 Overview__
### __● Entity Relationship Diagram__
- ![PCM_ERD](https://hp.sharepoint.com/:i:/t/BPSEngineeringDigitization/EWDqg5eOCqVCqI_h6MXt5sYBbsGHYNdoC5ZnH7DoYOUJSA?e=tT07zI)

### __● Database Name__
- PCM


### __● Table Extract__

#### 1. PCM_file

- Description  : contaim basic information
- Table_id  : PCM_file						
 
| Name | Type | Not Null | Description | Reference | Check | 
|:---|:---|:---|:---|:---|:---|
|:key: file_id  | string |`True`| Unique identifier to the testing record of each pcm report,auto-generation UUID format from the backend.Format: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx (32 hexadecimal characters and 4 hyphens) |  |  |
| file_name | string| `True`|Unique PCM report file name.<br>naming rule:<br>\[BIOS Version]\<scenario detail\>\_\<Code name>\_\<TDP>\_PCM_Report-<template verion\>\_\<Date>\_<Time\>.xlsx<br>Exapmle: [001900]S0_Kraken14_15W_PCM_Report-2.0.0_20221122_223055.xlsx |  |  |
| data_source | string |`True`| Which method to deal with PCM report.<br>format: starliner-web/ starliner-tool/ vcosmos ... |  |  |
| uploader | string |`True`| Mail format.|  |  |
| marketplace_id | string |`True`| Starliner marketplace id. |  |  |
| version | int |`True`| PCM report version. |  |  |
| UpdatedAt | timestamp |`True`| file upload time. <br>Format: YYYY-MM-DD hh:mm:ss |  |  |


#### 2. PCM_HDD

- Description  : HDD information
- Table_id  : PCM_HDD						
 
| Name | Type | Not Null | Description | Reference | Check | 
|:---|:---|:---|:---|:---|:---|
| file_id | string |`True`| Unique identifier to the testing record of each pcm report, auto-generation UUID format from the backend. |  [[pcm_file].[file_id]](#1-pcm_file)|  |
| function | string |`True` |The corresponding function of each value.|||
| HDD_supplier | string |`True`|The corresponding HDD Supplier information.|||
| HDD_PN | string |`False`|  The corresponding HDD PN information. |  |  |
| HDD_GB | int |`False`|  The corresponding HDD GB information (unit:GB). |  |  |


#### 3. PCM_LCD

- Description  : LCD information
- Table_id  : PCM_LCD						
 
| Name | Type | Not Null | Description | Reference | Check | 
|:---|:---|:---|:---|:---|:---|
| file_id | string |`True`| Unique identifier to the testing record of each pcm report, auto-generation UUID format from the backend. |  [[pcm_file].[file_id]](#1-pcm_file)|  |
| LCD_supplier | string |`False`|The corresponding LCD Supplier information.|||
| LCD_PN | string |`False`|The corresponding LCD PN information.|||


#### 4. PCM_RAM

- Description  : ram information
- Table_id  : PCM_RAM						
 
| Name | Type | Not Null | Description | Reference | Check | 
|:---|:---|:---|:---|:---|:---|
| file_id | string |`True`| Unique identifier to the testing record of each pcm report, auto-generation UUID format from the backend. |  [[pcm_file].[file_id]](#1-pcm_file)|  |
| ram_supplier | string |`True`|The corresponding ram Supplier information.|||
| ram_PN | string |`True`|The corresponding ram PN information.|||
| ram_GB | int |`True`|The corresponding ram PN information. (unit:GB)|||
| ram_GB_total | int |`True`|The corresponding number of rams. |||
| ram_type | string |`True`|The corresponding ram type information.|||


#### 5. PCM_platform_spec

- Description  : Platform Spec
- Table_id  : PCM_platform_spec				
 
| Name | Type | Not Null | Description | Reference | Check | 
|:---|:---|:---|:---|:---|:---|
| file_id | string |`True`| Unique identifier to the testing record of each pcm report, auto-generation UUID format from the backend. |  [[pcm_file].[file_id]](#1-pcm_file)|  |
| power_rail_index | string |`True`|Power rail index.|||
| common_power_rail_definition | string |`False`|The corresponding common power rail definition. |||
| power_rail_define | string |`False`|The corresponding  power rail definition of each project. |||
| total_power_target | float |`True`|The target value of each power rail in total (unit:W) |||
| s0_power_targete | float |`True`|The target value of each power rail in S0. (unit:W)|||
| MSC_power_target | float |`True`|The target value of each power rail in MSC. (unit:W)|||
| s5_power_target | float |`True`The target value of each power rail in S5. (unit:W)|||
| function | string |`True`|The corresponding function of each value.|||


#### 6. PCM_platform_config

- Description  : detailed platform information
- Table_id  : PCM_platform_config		
 
| Name | Type | Not Null | Description | Reference | Check | 
|:---|:---|:---|:---|:---|:---|
| file_id | string |`True`| Unique identifier to the testing record of each pcm report, auto-generation UUID format from the backend. |  [[pcm_file].[file_id]](#1-pcm_file)|  |
| pcm_names | string |`True`|Combine Pulsar name and watt of CPU, make a category for power BI.|||
| pulsar_name | string |`True`|Pulsar name information.|||
| test_start | timestamp |`True`|Start time of testing. <br>Format: YYYY-MM-DD hh:mm:ss |||
| test_end | timestamp |`True`|End time of testing. <br>Format: YYYY-MM-DD hh:mm:ss|||
| workweek | int |`True`|testing Work week. |||
| TDP | string |`True`|The corresponding CPU watt information of each report. (unit:W)|||
|scenario_detail | string |`True`|Power rail index|||
| scenario | string |`True`|Test detailed scenarion.|||
| UpdatedAt | timestamp |`True`|Datetime the record was last updated. <br>Format: YYYY-MM-DD hh:mm:ss |||

#### 7. PCM_config_data

- Description  : config infirmation of platform
- Table_id  : PCM_config_data		
 
| Name | Type | Not Null | Description | Reference | Check | 
|:---|:---|:---|:---|:---|:---|
| file_id | string |`True`| Unique identifier to the testing record of each pcm report, auto-generation UUID format from the backend.|[[pcm_file].[file_id]](#1-pcm_file)||
| configuration | string |`True`|Config item.|||
| content | string |`True`|Config Content.|||
| UpdatedAt | timestamp |`True`|Datetime the record was last updated. <br>Format: YYYY-MM-DD hh:mm:ss|||


#### 8. PCM_raw_data

- Description  : PCM calculated data
- Table_id  : PCM_raw_data				
 
| Name | Type | Not Null | Description | Reference | Check | 
|:---|:---|:---|:---|:---|:---|
| file_id | string |`True`| Unique identifier to the testing record of each pcm report, auto-generation UUID format from the backend. |  [[pcm_file].[file_id]](#1-pcm_file)|  |
| power_rail_index | string |`True`|Power rail index.|||
| power_rail_define | string |`False`|The corresponding  power rail definition of each project. |||
| value | float |`True`|Value (unit:W)|||
| power_state | string |`True`|The corresponding state of each value.|||
| UpdatedAt | timestamp |`True`|Datetime the record was last updated. <br>Format: YYYY-MM-DD hh:mm:ss|||


#### 9. PCM_raw_data_sheet

- Description  : PCM raw data
- Table_id  : PCM_raw_data_sheet			
 
| Name | Type | Not Null | Description | Reference | Check | 
|:---|:---|:---|:---|:---|:---|
| file_id | string |`True`| Unique identifier to the testing record of each pcm report, auto-generation UUID format from the backend. |  [[pcm_file].[file_id]](#1-pcm_file)|  |
| value| float |`True`|Value (unit:W)||`>= 0`|
| power_rail_define | string |`True`|The corresponding  power rail definition of each project.|||
| time | timestamp |`True`|Time of testing.<br>Format: YYYY-MM-DD hh:mm:ss|||
| power_state | string |`True`|The corresponding state of each value.|||
| time_id | string |`True`|unique identifier to the testing record of each test time.|||
| UpdatedAt | timestamp |`True`|Datetime the record was last updated. <br>Format: YYYY-MM-DD hh:mm:ss|||


#### 10. PCM_app

- Description  : app information
- Table_id  : PCM_app			
 
| Name | Type | Not Null | Description | Reference | Check | 
|:---|:---|:---|:---|:---|:---|
| file_id | string |`True`| Unique identifier to the testing record of each pcm report, auto-generation UUID format from the backend.|[[pcm_file].[file_id]](#1-pcm_file)||
| installed_apps | string |`False`|Description of App.|||
| publisher | string |`True`|Publisher information of App.|||
| version | string |`True`|App version.|||
| UpdatedAt | timestamp |`True`|Datetime the record was last updated. <br>Format: YYYY-MM-DD hh:mm:ss|||

#### 11. PCM_driver

- Description  : driver infirmation of platform
- Table_id  : PCM_driver			
 
| Name | Type | Not Null | Description | Reference | Check | 
|:---|:---|:---|:---|:---|:---|
| file_id | string |`True`| Unique identifier to the testing record of each pcm report, auto-generation UUID format from the backend. |  [[pcm_file].[file_id]](#1-pcm_file)|  |
| installed_drvs | string |`False`|Name of Driver.|||
| publisher | string |`True`|Publisher information of driver.|||
| version | string |`True`|Driver version.|||
| UpdatedAt | timestamp |`True`|Datetime the record was last updated. <br>Format: YYYY-MM-DD hh:mm:ss|||



## ⭐️Support

<p>&copy; 2022 HP inc. HW, Starliner.</p>


