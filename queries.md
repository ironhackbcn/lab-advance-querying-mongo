![Ironhack Logo](https://i.imgur.com/1QgrNNw.png)

# Answers

### 1. All the companies that it's name match 'Babelgum'. Retrieve only their `name` field.

db.companies.find({name:'Babelgum'},{name:1,\_id:0})

### 2. All the companies that have more than 5000 employees. Limit the search to 20 companies and sort them by **number of employees**.

db.companies.find({'number_of_employees':{\$gt:5000}}, {name:1,number_of_employees:1,\_id:0}).sort({number_of_employees:1}).limit(20)

### 3. All the companies founded between 2000 and 2005, both years included. Retrieve only the `name` and `founded_year` fileds.

db.companies.find({ "$and" : [{"founded_year" : {"$gte" : 2000}}, {"founded_year" : {"\$lte" : 2005}}]}, { "name" : 1,"\_id" : 0, "founded_year" : 1});

### 4. All the companies that had a Valuation Amount of more than 100.000.000 and have been founded before 2010. Retrieve only the `name` and `ipo` fields.

db.companies.find({ "$and":[{"ipo.valuation_amount":{"$gte":100000000},{"founded_year":{"\$lt":2010}]},{"name":1,"\_id":0,"ipo":0});

<!--duda: ¿Como llegar a valuation_amount dentro de ipo-->

### 5. All the companies that have less than 1000 employees and have been founded before 2005. Order them by the number of employees and limit the search to 10 companies.

db.companies.find({"$and":[{'number_of_employees':{"$lt":1000}},{"founded_year":{"\$lt":2005}}]}).sort({"number_of_employees":1}).limit(10)

<!--Funciona, pero ahora solo quiero solo con el nombre de la empresa y el founded year(pero hay un error de un } y no me sale:-->

db.companies.find({"$and":[{'number_of_employees':{'$lt':1000}},{'founded_year':{"\$lt":2005}}],{name:1,'founded_year':1,\_id:0}}).sort({'number_of_employees':1}).limit(10)

<!--error: SyntaxError: expected property name, got '{'-->

### 6. All the companies that don't have any `partners` (partners is an array).

db.companies.find({"\$nin":['partners']})

<!--error: [js] SyntaxError: expected expression, got ']' :
@(shell):1:34-->

### 7. All the companies that have a null type of value on the `category_code` field.

db.companies.find({"\$eq":[{'category_code':null}])

<!-- $eq: Matches values that are equal to a specified value.No sale -->

### 8. All the companies that have at least 100 employees but less than 1000. Retrieve only the `name` and `number of employees` fields.

db.companies.find({"$and":[{'number_of_employees':{'$gte':100}},{'number_of_employees':{\$lt:1000}}]},{name:1,\_id:0,number_of_employees:1})

### 9. Order all the companies by their IPO valuation_amount descendently.

db.companies.find({ }).sort(ipo.valuation_amount:-1);

<!--No estoy seguro de si me sale bien-->

### 10. Retrieve the 10 companies with more employees, order by the `number of employees`

db.companies.find().sort('number_of_employees':1).limit(10)

### 11. All the companies founded on the second semester of the year. Limit your search to 1000 companies.

db.companies.find({"founded_month":{"\$gte":6}},{'name':1}).limit(1000);

<!-- Sale Ok, pero si pongo el id:0 no me sale => db.companies.find({"founded_month":{"$gte":6}},{'name':1,'_id':0,'founded_month:1'}).limit(1000);
2019-10-15T19:35:57.504+0200 E  QUERY    [js] SyntaxError: missing : after property id :
@(shell):1:82 -->

### 12. All the companies that have been 'deadpooled' after the third year.

db.companies.find({"deadpooled_year":{'\$gt':3}})

<!-- Funciona, pero si quiero que solo me salga el nombre y el año deadpool sale error -->

### 13. All the companies founded before 2000 that have and acquisition amount of more than 10.000.000

db.companies.find({$and:[{'founded_year':{$lt:2000}},{'acquisition.price_amount':{'\$gt':10000000}}]},{name:1, \_id:0})

### 14. All the companies that have been acquired after 2012, order by the acquisition amount, and retrieve only their `name` and `acquisiton` field.

<!-- Your Code Goes Here -->

db.companies.find({'acquisition_date':{'\$gt':2015}},{'name':1,'acqusition':1).sort('acquisition_amount');

<!--expected property name, got '{'?-->

### 15. Order the companies by their `founded year`, retrieving only their `name` and `founded year`.

db.companies.find({'name':1,'founded_year':1}).sort('founded_year')

<!-- Error: "Failed to parse: sort: \"founded_year\" -->

### 16. All the companies that have been founded on the first seven days of the month, including the seventh. Sort them by their `aquisition price` descendently. Limit the search to 10 documents.

db.companies.find({'acquisition.acquired_day':{ \$lte:7}}).sort('acquisition.price_amount':-1).limit(10);

### 17. All the companies on the 'web' `category` that have more than 4000 employees. Sort them by the amount of employees in ascendant order.

db.companies.find({$eq:['category_code':'web'],{'number_of_employees':{$gte:4000}).sort('number_of_employees':-1);

<!-- No me sale -->

### 18. All the companies which their acquisition amount is more than 10.000.000, and currency are 'EUR'.

db.companies.find({$and:[{'acquisition.price_amount':{'$gte':10000000}},{'acquisition.price_currency_code':{\$eq:"EUR"}}]})

<!-- SyntaxError: missing ) after argument list : -->

db.companies.find({ $and : [{"founded_year" : {"$gte" : 2000}}, {"founded_year" : {"\$lte" : 2005}}]}, { "name" : 1,"\_id" : 0, "founded_year" : 1});

### 19. All the companies that have been acquired on the first trimester of the year. Limit the search to 10 companies, and retrieve only their `name` and `acquisition` fields.

db.companies.find({'founded_month':{\$lte:3}},{name:1,\_id:0,acquisition:0}).limit(10)

<!-- Error: error: {
	"ok" : 0,
	"errmsg" : "Projection cannot have a mix of inclusion and exclusion.",
	"code" : 2,
	"codeName" : "BadValue" -->

### 20. All the companies that have been founded between 2000 and 2010, but have not been acquired before 2011.

db.companies.find({$and:[{'founded_year':{$gte:2000},{'founded_year':{$lte:2000}},{'acquisition.acquired_year':{$gte:2011}}]})
