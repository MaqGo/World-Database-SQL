# 🌍 World Database SQL Queries

This project contains a collection of SQL queries executed on the MySQL World Sample Database using MySQL Workbench. 

This project demonstrates how to:

- Retrieve, filter, and aggregate data.
- Join tables to combine related data.
- Sort and group results for better insights.
- Use scenarios to solve real-world data problems.

# 🛠 Tools Used

- MySQL Workbench
- MySQL (World Sample Database)
- SQL (Structured Query Language)
  
# 📁 Tables Used

- city
- country
  
# 📊 SAMPLE QUARIES

# 1. Count Cities in the USA

Count Cities in USA: Scenario: You've been tasked with conducting a demographic analysis of cities in the United States. Your first step is to determine the total number of cities within the country to provide a baseline for further analysis. 

💻 SQL Query:

SELECT COUNT(Name), CountryCode
FROM city                      
WHERE CountryCode = 'USA';     

- 📌 Result: 274 cities in the USA.

# 2. Countries by Highest Life Expectancy

Country with Highest Life Expectancy: Scenario: As part of a global health initiative, you've been assigned to identify the country with the highest life expectancy. This information will be crucial for prioritising healthcare resources and interventions. 

💻 SQL Query:

SELECT Name, lifeExpectancy                       
FROM country                                      
ORDER BY lifeExpectancy DESC;                     

- 📌 Result: Andorra, Macao, San Marino, Japan, etc.
  
# 3. Cities Starting with "New"

New Year Promotion: Featuring Cities with 'New : Scenario: In anticipation of the upcoming New Year, your travel agency is gearing up for a special promotion featuring cities with names including the word 'New'. You're tasked with swiftly compiling a list of all cities from around the world. This curated selection will be essential in creating promotional materials and enticing travellers with exciting destinations to kick off the New Year in style. 

💻 SQL Query:

SELECT Name
FROM City
WHERE Name LIKE "New%";

- 📌 Result: Newcastle, New Orleans, etc.

# 4. Top 10 Most Populated Cities

Display Columns with Limit (First 10 Rows): Scenario: You're tasked with providing a brief overview of the most populous cities in the world. To keep the report concise, you're instructed to list only the first 10 cities by population from the database. 

💻 SQL Query:

SELECT name, population
FROM city
ORDER BY population DESC
LIMIT 10;

- 📌 Result: Cities like Mumbai, Seoul, São Paulo, Shanghai, etc.
  
# 5. Cities with population greater than or equal to 2 million, ordered by population descending

Cities with Population Larger than 2,000,000: Scenario: A real estate developer is interested in cities with substantial population sizes for potential investment opportunities. You're tasked with identifying cities from the database with populations exceeding 2 million to focus their research efforts. 

💻 SQL Query:

SELECT name, population
FROM city
WHERE population >= 2000000
ORDER BY population DESC;

- 📌 Result:
| Mumbai (Bombay)  | 10500000   |
| Seoul            | 9981619    |
| São Paulo        | 9968485    |
| Shanghai         | 9696300    |
| Jakarta          | 9604900    |
| Karachi          | 9269265    |
| Istanbul         | 8787958    |
| Ciudad de México | 8591309    |
| Moscow           | 8389200    |
| New York         | 8088276    |

# 6. Query 3: Cities with Names Starting with ‘Be’

Cities Beginning with 'Be' Prefix: Scenario: A travel blogger is planning a series of articles featuring cities with unique names. You're tasked with compiling a list of cities from the database that start with the prefix 'Be' to assist in the blogger's content creation process. 

💻 SQL Query:

SELECT Name
FROM City
WHERE Name LIKE 'Be%';

- 📌 Result:
Béjaïa, Béchar, Benguela...             

# 7. Cities with population between 500,000 and 1,000,000

Cities with Population Between 500,000-1,000,000: Scenario: An urban planning committee needs to identify mid-sized cities suitable for infrastructure development projects. You're tasked with identifying cities with populations ranging between 500,000 and 1 million to inform their decision-making process. 

💻 SQL Query:

SELECT Name, Population
FROM City
WHERE Population BETWEEN 500000 AND 1000000;

- 📌 Result:
Amsterdam — 731200
Rotterdam — 593321
Adelaide — 978100
(and more, total: 33 rows returned)

# 8. List all city names in ascending order

 Display Cities Sorted by Name in Ascending Order: Scenario: A geography teacher is preparing a lesson on alphabetical order using city names. You're tasked with providing a sorted list of cities from the database in ascending order by name to support the lesson plan. 

💻 SQL Query:

SELECT Name
FROM City
ORDER BY Name ASC;

- 📌 Result:
[San Cristóbal de] la Laguna's-Hertogenbosch
A Coruña (La Coruña)
Abbotsford
(and more, total: 1000 rows returned)

# 9. City with the largest population

Most Populated City: Scenario: A real estate investment firm is interested in cities with significant population densities for potential development projects. You're tasked with identifying the most populated city from the database to guide their investment decisions and strategic planning. 

💻 SQL Query:

SELECT Name, Population
FROM City
ORDER BY Population DESC
LIMIT 1;

- 📌 Result:
Mumbai — 10,500,000

# 10. Count of each city name grouped and sorted alphabetically

City Name Frequency Analysis: Supporting Geography Education Scenario: In a geography class, students are learning about the distribution of city names around the world. The teacher, in preparation for a lesson on city name frequencies, wants to provide students with a list of unique city names sorted alphabetically, along with their respective counts of occurrences in the database. You're tasked with this sorted list to support the geography teacher. 

💻 SQL Query:

SELECT COUNT(name) AS Occurrences, name
FROM City
GROUP BY name
ORDER BY name ASC;
- 📌 Result:
1 | [San Cristóbal de] la Laguna
1 | 's-Hertogenbosch
(and more, total: 101 rows returned)

# 11. City with Smallest Population

City with the Lowest Population: Scenario: A census bureau is conducting an analysis of urban population distribution. You're tasked with identifying the city with the lowest population from the database to provide a comprehensive overview of demographic trends. 

💻 SQL Query:

SELECT name, population 
FROM city 
ORDER BY Population ASC 
LIMIT 1;

- 📌 Result:
 Adamstown | 42         |

# 12. Country with Largest Population

Country with Largest Population: Scenario: A global economic research institute requires data on countries with the largest populations for a comprehensive analysis. You're tasked with identifying the country with the highest population from the database to provide valuable insights into demographic trends. 

💻 SQL Query:

SELECT Name, population
FROM country
ORDER BY Population DESC
LIMIT 1;

- 📌 Result:
 China | 1,277,558,000 

# 13. Capital City of Spain

Capital of Spain: Scenario: A travel agency is organising tours across Europe and needs accurate information on capital cities. You're tasked with identifying the capital of Spain from the database to ensure itinerary accuracy and provide travellers with essential destination information. 

💻 SQL Query:

SELECT country.name AS Country, city.name AS City
FROM city
LEFT JOIN country
ON city.id = country.capital
WHERE capital IS NOT NULL
AND country.name = 'Spain';

- 📌 Result:
  Spain   | Madrid 

# 14. Cities and Their Continents

Cities in Europe: Scenario: A European cultural exchange program is seeking to connect students with cities across the continent. You're tasked with compiling a list of cities located in Europe from the database to facilitate program planning and student engagement.

💻 SQL Query:

SELECT city.name, continent
FROM city
RIGHT JOIN country
ON city.countrycode = country.code;

- 📌 Result:

| Oranjestad     | North America |
| Kabul          | Asia          |
| Gandahar       | Asia          |
| Herat          | Asia          |
| Mazar-e-Sharif | Asia          |
| Luanda         | Africa        |
| Huambo         | Africa        |
| Lobito         | Africa        |
| Benguela       | Africa        |
| Namibe         | Africa        |
| South Hill     | North America |

# 15. Average Population by Country

Average Population by Country: Scenario: A demographic research team is conducting a comparative analysis of population distributions across countries. You're tasked with calculating the average population for each country from the database to provide valuable insights into global population trends. 

💻 SQL Query:

SELECT Name, AVG(Population)
FROM Country
GROUP BY Name;

- 📌 Result:
| Aruba                | 103000.0000     |
| Afghanistan          | 22720000.0000   |
| Angola               | 12878000.0000   |
| Anguilla             | 8000.0000       |
| Albania              | 3401200.0000    |
| Andorra              | 78000.0000      |
| Netherlands Antilles | 217000.0000     |
| United Arab Emirates | 2441000.0000    |
| Argentina            | 37032000.0000   |
| Armenia              | 3520000.0000    |
| American Samoa       | 68000.0000      |
| ...                  | ...             |

# 16. Country Capitals with Population

Capital Cities Population Comparison: Scenario: A statistical analysis firm is examining population distributions between capital cities worldwide. You're tasked with comparing the populations of capital cities from different countries to identify trends and patterns in urban demographics. 

💻 SQL Query:

SELECT country.name AS Country, city.name AS City, city.population
FROM city
LEFT JOIN country
ON city.id = country.capital
WHERE capital IS NOT NULL;

- 📌 Result:
| Aruba                | Oranjestad       | 29,034     |
| Afghanistan          | Kabul            | 1,780,000  |
| Angola               | Luanda           | 2,022,000  |
| Anguilla             | The Valley       | 595        |
| Albania              | Tirana           | 270,000    |
| Andorra              | Andorra la Vella | 21,189     |
| Netherlands Antilles | Willemstad       | 23,945     |
| United Arab Emirates | Abu Dhabi        | 398,695    |
| Argentina            | Buenos Aires     | 2,982,146  |
| Armenia              | Yerevan          | 1,248,700  |
| American Samoa       | Fagatogo         | 2,323      |
| ...                  | ...              | ...        |

# 17. Countries Ordered by Population Density (Lowest First)

Countries with Low Population Density: Scenario: An agricultural research institute is studying countries with low population densities for potential agricultural development projects. You're tasked with identifying countries with sparse populations from the database to support the institute's research efforts. 

💻 SQL Query:

SELECT 
  Name AS Country,
  Population,
  SurfaceArea,
  ROUND(Population / SurfaceArea, 2) AS PopulationDensity
FROM 
  country
WHERE 
  Population IS NOT NULL AND SurfaceArea > 0
ORDER BY 
  PopulationDensity ASC
LIMIT 20;

- 📌 Result:
| South Georgia and the South Sandwich Is | 0          | 3903.00     | 0.00              |
| British Indian Ocean Territory          | 0          | 78.00       | 0.00              |
| Antarctica                              | 0          | 13120000.00 | 0.00              |
| French Southern territories             | 0          | 7780.00     | 0.00              |
| Bouvet Island                           | 0          | 59.00       | 0.00              |
| United States Minor Outlying Islands    | 0          | 16.00       | 0.00              |
| Heard Island and McDonald Islands       | 0          | 359.00      | 0.00              |
| Greenland                               | 56000      | 2166090.00  | 0.03              |
| Svalbard and Jan Mayen                  | 3200       | 62422.00    | 0.05              |
| ...                                     | ...        | ...         | ...               |

  
# 18.Cities Ordered by GDP Per Capita

Cities with High GDP per Capita: Scenario: An economic consulting firm is analysing cities with high GDP per capita for investment opportunities. You're tasked with identifying cities with above-average GDP per capita from the database to assist the firm in identifying potential investment destinations. 

💻 SQL Query:

SELECT 
  Name AS City,
  CountryCode,
  Country,
  Population AS CityPopulation,
  (
    SELECT AVG(GNP / Population)
    FROM country
    WHERE Population > 0 AND GNP IS NOT NULL
  ) AS GDPPerCapita
FROM 
  city
ORDER BY 
  GDPPerCapita DESC;
  
- 📌 Result:
| Zürich                   | CHE         | Switzerland | 336800         | 0.04         |
| Geneve                   | CHE         | Switzerland | 173500         | 0.04         |
| Basel                    | CHE         | Switzerland | 166700         | 0.04         |
| Bern                     | CHE         | Switzerland | 122700         | 0.04         |
| Lausanne                 | CHE         | Switzerland | 114500         | 0.04         |
| Luxembourg \[Luxembourg] | LUX         | Luxembourg  | 80700          | 0.04         |
| Saint George             | BMU         | Bermuda     | 1800           | 0.04         |
| Hamilton                 | BMU         | Bermuda     | 1200           | 0.04         |
| Bandar Seri Begawan      | BRN         | Brunei      | 21484          | 0.04         |

# 19. Top Cities by Population with Offset

Display Columns with Limit (Rows 31-40): Scenario: A market research firm requires detailed information on cities beyond the top rankings for a comprehensive analysis. You're tasked with providing data on cities ranked between 31st and 40th by population to ensure a thorough understanding of urban demographics.

💻 SQL Query:

SELECT
  Name AS City,
  CountryCode,
  Population
FROM
  city
ORDER BY
  Population DESC
LIMIT 10 OFFSET 30;

- 📌 Result:
| Shenyang            | CHN         | 4,265,200  |
| Kanton \[Guangzhou] | CHN         | 4,256,300  |
| Singapore           | SGP         | 4,017,733  |
| Ho Chi Minh City    | VNM         | 3,980,000  |
| Chennai (Madras)    | IND         | 3,841,396  |
| Pusan               | KOR         | 3,804,522  |
| Los Angeles         | USA         | 3,694,820  |
| Dhaka               | BGD         | 3,612,850  |
| Renrka              | DEU         | 3,386,467  |

# 📚 Learning Highlights

✅ Practice advanced SELECT, WHERE, ORDER BY, GROUP BY, and JOIN operations.
✅ Explore real-world use cases for SQL queries.
✅ Build a foundation for database analysis and reporting.

# 📷 Screenshots

Query outputs are demonstrated in the screenshots located in the repository's /screenshots folder.

# 📄 License

This project is open source and available under the MIT License.












