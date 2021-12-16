# CS623-Project---12-15
This is a Simple Project of implementing the database to run the transactions. We have used Java and PostgreSQL. Accessing a PostgreSQL database using Java requires us to rely on the JDBC. On ourlocalhost system, we created a database named mydb and create a table product, stock and depot. To create a product table in pgAdmin we run the input in the query editor:
CREATE TABLE  IF NOT EXISTS PRODUCT +
       (PROD CHAR(50) PRIMARY KEY NOT NULL,                   	   NAME TEXT NOT NULL, +
       PRICE INT NOT NULL)
We need to set up a database connection. We did through the following
Connection connection = null;
        String host="localhost";
        String port="5432";
        String db_name="posts";
        String username="postgres";
        String password="new_password";
        try {
            Class.forName("org.postgresql.Driver");
            connection = DriverManager.getConnection("jdbc:postgresql://"+host+":"+port+"/"+db_name+"", ""+username+"", ""+password+"");
To add a product to database we used the statement INSERT INTO PRODUCT (ID NAME PRICE ) VALUES(P100,cd,5); and to add the same product to the stock database we also used the transaction statement INSERT INTO STOCK (PROD,DEP,QUANTITY) VALUES ('P100', 'D2',50 );
To delete the product p1 from products table we used the first connect to the database and table products and delete the product p1 using the following statement DELETE FROM product WHERE id = 'P1' Once the product P1 Is deleted the stock on P1 will also be automatically deleted due to the relation described during creation of the product table i.e ON DELETE CASCADE. To delete d1 from database we used the statement...DELETE FROM depot WHERE id = 'D1' which will in turn delete the whole stock whose depot Id due to the relation defined during creation of the table ie ON DELETE CASCADE
