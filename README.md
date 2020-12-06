# SQL.js standalone
Run SQL directly in the browser, in web apps or hybrid applications all with one single script.

This is a compilation into a standalone, locally executable script of SQL.js javascript code and required WebAssembly (wasm) from SQL.js project ([https://github.com/sql-js/sql.js](https://github.com/sql-js/sql.js)).

Running SQL in a html file is very easy, even without a web server. Just copy the code below into a html file, and open it in your browser:
```js

<script src="sqljs-standalone.js"></script>
<script>
	initSqlJs().then(SQLJS=>{
		// Create a table and insert 3 rows
		db = new SQLJS.Database();
		db.run("CREATE TABLE Products(pro_id INT PRIMARY KEY, name VARCHAR(255))");
		db.run("INSERT INTO Products VALUES (?,?), (?,?), (?,?)", [1, 'Product 1', 2, 'Product 2', 3, 'Product 3']);
		// Query database
		var res = db.exec("SELECT * FROM Products");
		console.log("My products = " + JSON.stringify(res[0].values));
	});
</script> 
```
## To go further
Data can be persisted and synchronized automatically with a SQL/NoSQL backend database using the SyncProxy sync gateway 
([https://www.syncproxy.com](https://www.syncproxy.com)).
