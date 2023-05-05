Download Link: https://assignmentchef.com/product/solved-csi235-lab3
<br>
<h2>Task 1  Verification of consistency constraints and generation of derived data</h2>

<strong> </strong>Implement a stored PL/SQL procedure

INSERT_ITEM(order_key,part_key,supplier_key,quantity,price,             discount,tax)

that enforces a consistency constraint listed below before inserting a row to a relational table LINEITEM.

<ul>

 <li>The same part manufactured by the same supplier cannot be included more than one time in the same order.</li>

</ul>

The procedure must also generate the values of missing attributes before insertion of a row.

<ul>

 <li>A value of an attribute L_LINENUMBER must be automatically generated.</li>

 <li>A value of attribute L_SHIPDATE must be tomorrow’s date.</li>

 <li>A value of attribute L_RECEIPTDATE must be one week after shipment date.</li>

 <li>The values of the other attributes are up to you. A simple solution is to use 0 for the columns of type NUMBER, empty string ” for CHAR or VARCHAR and today’s date for DATE.</li>

</ul>

If a consistency constraint listed above validates well, then the procedure must make an insertion of a row permanent in a database. If a consistency constraint does not validate well, the procedure must not insert a row and it must display an error message.

When the implementation of a procedure INSERT_ITEM is completed, create SQL script solution1.sql that stores the procedure in a data dictionary and tests the procedure with EXECUTE statements. Testing must be performed in the following way.

<ul>

 <li>One successful insertion must be performed into an already existing order.</li>

 <li>One successful insertion must be performed into a new order, and it means that you must insert a new order into a relational table ORDERS</li>

 <li>One unsuccessful insertion must be performed into an already existing order.</li>

 <li>Use SELECT statement to display the successfully inserted rows.</li>

</ul>




Your report must include a listing of all PL/SQL statements processed. To achieve that put the following SQLcl commands:




SPOOL solution1

SET SERVEROUTPUT ON

SET ECHO ON

SET FEEDBACK ON

SET LINESIZE 200

SET PAGESIZE 400

SET SERVEROUTPUT ON




at the beginning of SQL script and




SPOOL OFF




at the end of SQL script.




<h2>Deliverables</h2>

A file solution1.lst with a report from the implementation and testing of a stored procedure INSERT_ITEM.  A report must have no errors and it must list all PL/SQL and SQL statements processed.

<u>                                                                                                                                                </u>

<h2>Task 4 (1 mark) Simplification of SQL with a stored function</h2>

<strong> </strong>

The following SELECT statement lists the names and addresses of customers who either submitted more than 20 orders or who submitted no orders at all.




SELECT CUSTOMER.C_CUSTKEY, COUNT(ORDERS.O_CUSTKEY) CNT

FROM CUSTOMER LEFT OUTER JOIN ORDERS

ON CUSTOMER.C_CUSTKEY = ORDERS.O_CUSTKEY

GROUP BY CUSTOMER.C_CUSTKEY

HAVING COUNT(ORDERS.O_CUSTKEY) &gt; 20 OR

COUNT(ORDERS.O_CUSTKEY) = 0

ORDER BY CNT ASC;




Implement a stored PL/SQL function that can be used in SELECT statement such that the new SELECT statement retrieves the same information as the old one and it consists of the clauses SELECT, FROM, WHERE, and ORDER BY only. The new SELECT does not use GROUP BY and HAVING clauses. Additionally, the new SELECT statement does not use an operation of LEFT OUTER JOIN.




When ready, implement a script solution2.sql that performs the following sequence of actions.




<ul>

 <li>First, the script processes SELECT statement give above,</li>

 <li>Next, the script stores PL/SQL function in a data dictionary,</li>

 <li>Next, the script processes SELECT statement that uses the stored function to retrieve the same results as the original statement,</li>

 <li>Finally, the script drops the stored function.</li>

</ul>




If you have the temptations to use DBMS_OUTPUT with PUT_LINE method then it is a very bad idea and such idea will not bring you a good evaluation.




Process SQL script solution2.sql and save a report from processing in a file solution2.lst.




Your report must include a listing of all PL/SQL statements processed. To achieve that put the following SQL*Plus commands:




SPOOL solution2

SET ECHO ON

SET FEEDBACK ON

SET LINESIZE 100

SET PAGESIZE 200

SET SERVEROUTPUT ON




at the beginning of SQL script and




SPOOL OFF




at the end of SQL script.




<h2>Deliverables</h2>

A         file solution2.lst with             a          report   from    processing       of         SQL     script solution2.sql. A report must have no errors and it must list all PL/SQL and SQL statements processed.