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
* [Table Buffers](#Table-Buffers)
* Program Buffer
* SAPgui Buffers
* [Roll and Paging Buffers](#Roll-and-Paging-Buffers)
* SAP Calendar Buffer
* SAP Cursor Cache

# Repository Buffers

***Will need more explanation on this topic***

***Also known as Nametab Buffers***


The name table contains the table and field definitions that are activated in the SAP System.

An entry is made in the Repositroy buffer when a *mass activator* or a *user* requests to *activate a table.*
    
* What does it mean when a table is activated?

Once activated, the corresponding name table is generated from the information that is managed in the repository
* Does this essentially mean that once we have retrieved the table information from the database, it is then stored in the Repositroy Buffer to optimize our system when accessing that table?

When the newly created table is being stored in the Repository Buffer, the description of the table is distributed among severl other tables including:
* Field Definition
* Data Element Definition
* Domain Definition

All of this information is summaried in the name table in the following db tables:
* DDNTT (Table definitons)
* DDNTF (Field descriptions)

The Repositroy Buffer consists of four buffers in shared memory:
| | | |
|---|---|---|
| Table Definitions | TTAB Buffer | Table DDNT |
| Field Descriptions | FTAB Buffer | Table DDNTF |
| Initial Record Layouts | IREC Buffer | Contains the record layout initialized depending on the field type |
| Short Nametab | SNTAB buffer | A short summary of TTAB and FTAB buffers |

In the above table, the Short nametab and Initial record layouts are not saved in the databse, they are derived from contents of tables DDNTT and DDNTF

When a user requests access to a table, the DB access agent (embedded in each work process) will read the Short nametab buffer for info about that specific table.

If there is insufficient information (i.e SELECT statemetn uses a non-primary key) it will access the table definitions buffer and then the field descriptions buffer.

By reading the repository buffers, the db access agent knows whether the table is buffered or not.

After obtaining all the required information, the system is able to determine where to pull the data from:
* Partial Buffer
* Generic Buffer
* Database

The IREC buffer is read:
* When a REFRESH command is executed in an ABAP program
* At an INSERT command, when a record is created in the buffers before the data is inserted and the fields are initialized with the values found in IREC buffer

# Roll and Paging Buffers
Roll and Paging buffers are the preferred working areas of the roll and paging areas for an instance (AS)

The remaining area is located on disk as roll and paging files.

The user context is stored in the extended memory and the roll area (When the johb is "rolled out" of a work process).

Roll and Paging / Extneded Memory areas have different tasks they are used for:
* **Roll and Paging Area** - Stores special data for the ABAP processor
* **Extended Memory** - Stores a large portion of the internal tables of a program

# T-Codes
se11 - Create a Database Table


# Acronyms

***ABAP: Advanced Business Application Programming***

***AS: Application Server***

***TTAB: Table Buffer***

***FTAB: Field Descriptors***

***IREC: Initial Record Layout***

***SNTAB: Short Nametab***
