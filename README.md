# CREATED BY: Jeffery Sole
# DATE: 05/12/2023
# CONTENT: KochaSoft SAP Buffer Learning Material
##### ** **All content in this page is publicly available information provided by SAP** **

### Table of Contents:
1. [Introduction to ABAP Memory](#Introduction)
2. [Memory Buffers](#Memory-Buffer)
3. [Acronyms](#Acronyms)
4. [Useful T-Codes](#T-Codes)

# Introduction
SAP has two different types of memory, ABAP memory and SAP memory. ABAP memory is a memory area within **ABAP sessions** which can be accessed by different programs of a **call sequence**

To access this memory, you must use the statements **Export** and **Import**

The data stored in ABAP memory is persistant as long as the **top level transaction** of the call sequence is running. This is how ABAP memory is used as temporary memory. It runs as long as it is needed through user transactions, and then free's itself after it has performed its tasks and the session is ended.

In order to understand ABAP memory further, we should understand [ABAP session's](#ABAP-Sessions)

# ABAP Sessions

ABAP Sessions are instances created for user sessions in AS (Application Server) ABAP which use ABAP memory as a separate memory area.

When ABAP Sessions are created, there are some rules which are to be followed:
* Maximum number of ABAP sessions per user session: 16
* Each GUI Window is associated with its own ABAP session
    * ***Does this mean we are limited to only 16 GUI windows per session?***

ABAP Program's are children of Internal Sessions

## Buffer Types

SAP has several buffer types which include

* [Repository Buffers](#Repository-Buffers)
* Table Buffers
* Program Buffer
* SAPgui Buffers
* Roll and Paging Buffers
* SAP Calendar Buffer
* SAP Cursor Cache

# Repository Buffers

***Will need more explanation on this topic***

***Also known as Nametab Buffers***


The name table contains the table and field definitions that are activated in the SAP System.

An entry is made in the Repositroy buffer when a *mass activator* or a *user* requests to *activate a table.*
    
* What does it mean when a table is activated?

Once activated, the corresponding name table is generated from the information that is managed in the repository
* Does this essentially mean that once we have retrieved the table information from the database, it is then stored in the Repositroy Buffer?

# T-Codes
se11 - Create a Database Table


# Acronyms

***ABAP: Advanced Business Application Programming***
