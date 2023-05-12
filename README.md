# CREATED BY: Jeffery Sole
# DATE: 05/12/2023
# CONTENT: KochaSoft SAP Buffer Learning Material
##### ** **All content in this page is publicly available information provided by SAP** **

### Table of Contents:
1. [Introduction to ABAP Memory](#Introduction)
2. [Memory Buffers](#Memory-Buffer)
3. [](#Part-C)
4. [](#Part-D)

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

## Buffer Types

SAP uses memory buffers in order to reserve memory locations to optimize performance when users are performing transactions. SAP's main memory type which allows for temporary memory allocation is called ABAP memory

***ABAP: Advanced Business Application Programming***
