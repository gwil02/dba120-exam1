Exercise 1:

INSERT INTO terms
	(terms_id, terms_description, terms_due_days)
VALUES
	 (6, 'Net due 120 days', 120)

This query added a row to the terms table.

![ch5_1_results](https://user-images.githubusercontent.com/114038855/219128078-7b7db83f-a505-4021-ad1f-2f96c204edc6.png)

Exercise 2:

UPDATE terms
SET terms_description = 'Net due 125 days', terms_due_days = 125
WHERE terms_description = 'Net due 120 days'

This query updated two columns from the previous query's result. 

![ch5_2_results](https://user-images.githubusercontent.com/114038855/219128623-024f39a0-ff42-4809-adae-815e48f59c32.png)

Exercise 3:

DELETE FROM terms
WHERE terms_description = 'Net due 125 days';

This query deleted the previous query's result. 

![ch5_3_results](https://user-images.githubusercontent.com/114038855/219128795-679d6a11-1d43-4af7-a27c-cc18fb59cb2b.png)

Exercise 4:

INSERT INTO invoices 
VALUES (DEFAULT, 32, 'AX-014-027', 20180801, 434.58, 0.00, 0.00, 2, 20180831, NULL);

This query inserted a row into the invoices table.

![ch5_4_results](https://user-images.githubusercontent.com/114038855/219128990-544c1db1-55ca-4ab7-bb8e-f5f948a7f858.png)

Exercise 5: 

INSERT INTO invoice_line_items
VALUES (118, 1, 160, 180.23, 'Hard Drive'),
        (118, 2, 527, 254.35, 'Exchange Server Update')
        
This query inserted two rows into the invoice line items table that has the same invoice ID as exercise 4's result.

![ch5_5_results](https://user-images.githubusercontent.com/114038855/219129282-55764081-20e6-42aa-b515-6556d6507c9c.png)

Exercise 6:

UPDATE invoices
SET credit_total = invoice_total *.1,
	  payment_total = invoice_total - credit_total
WHERE invoice_id = 118

This query updated the query from exercise 4's result so that the credit_total column would be 10$ of the invoice total column, and the payment total and credit total columns are equal to the invoice total column.

![ch5_6_results](https://user-images.githubusercontent.com/114038855/219130030-6d4ceb76-a964-4a79-9c5e-50670fbeb6f4.png)

Exercise 7:

UPDATE vendors
SET default_account_number = 403
WHERE vendor_id = 44

This query updates all rows in the vendors table with the vendor id of 44 to have the account number 403.

![ch5_7_results](https://user-images.githubusercontent.com/114038855/219130215-e50e4b26-77fb-4614-91a2-0dcb4ffd327e.png)

Exercise 8:

UPDATE invoices
SET terms_id = 2
WHERE vendor_id in
  (SELECT vendor_id
  FROM vendors
  WHERE default_terms_id = 2);
  
This query changes the terms_id column to 2 for every row that is for a row in the vendors table with the terms id of 2.

![ch5_8_results](https://user-images.githubusercontent.com/114038855/219130795-57d14692-5eae-4cd6-ade1-2fb1f8cefe7a.png)

Exercise 9:

DELETE FROM invoice_line_items WHERE invoice_id=118;
DELETE FROM invoices WHERE invoice_id=118

This query chains two delete queries to remove all rows from the invoices table that have the invoice id of 118.

![ch5_9_results](https://user-images.githubusercontent.com/114038855/219131002-6cd678d2-0f62-402b-bbf4-156b9c1d0393.png)

