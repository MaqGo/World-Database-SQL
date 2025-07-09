# 🌍 World Database SQL Queries

This project contains a collection of SQL queries executed on the MySQL World Sample Database using MySQL Workbench.

# 🛠 Tools Used

- MySQL Workbench
- MySQL (World Sample Database)
- SQL (Structured Query Language)
  
# 📁 Tables Used

- city
- country
  
# 📊 Sample Queries

# 1. Count Cities in the USA
SELECT COUNT(Name), CountryCode
FROM city
WHERE CountryCode = 'USA';
- 📌 Result: 274 cities in the USA.

# 2. Countries by Highest Life Expectancy
SELECT Name, lifeExpectancy
FROM country
ORDER BY lifeExpectancy DESC;
- 📌 Result: Top countries include Andorra, Macao, San Marino, Japan, etc.

# 3. Top 10 Most Populated Cities
SELECT name, population
FROM city
ORDER BY population DESC
LIMIT 10;
- 📌 Result: Cities like Mumbai, Seoul, São Paulo, Shanghai, etc.

# 📌 Notes

Be sure to check for column names and case sensitivity in queries.
Use aliases for better readability in complex queries.
This project is for SQL learning and demonstration purposes.
# 📷 Screenshots

Query outputs are demonstrated in the screenshots located in the repository's /screenshots folder.

# 📄 License

This project is open source and available under the MIT License.












