query = """
SELECT *
FROM apexplanet
LIMIT 10;
"""
pd.read_sql(query, conn)

		Order_ID	Order_Date	Customer_ID	Customer_Name	Age	Gender	City	Product	Category	Quantity	Unit_Price	Total_Sales
0	ORD100002	2025-02-25	CUST5529	Customer_227	30.0	Female	Bengaluru	Rice	Grocery	7	2829.77	19808.39
1	ORD100003	2025-10-14	CUST3127	Customer_182	63.0	Male	Bengaluru	Book	Education	5	27906.16	139530.80
2	ORD100004	2025-05-13	CUST8887	Customer_487	62.0	Female	Bengaluru	Book	Education	8	37491.06	299928.48
3	ORD100005	2025-12-02	CUST2515	Customer_470	65.0	Female	Kolkata	Mobile	Electronics	9	28541.36	256872.24
4	ORD100006	2025-11-20	CUST4796	Customer_380	44.0	Male	Bengaluru	Rice	Grocery	10	14036.59	140365.90
5	ORD100007	2025-12-31	CUST3952	Customer_71	40.0	Female	Hyderabad	Laptop	Electronics	9	35947.47	323527.23
6	ORD100008	2025-10-14	CUST1758	Customer_335	61.0	Male	Patna	Mobile	Electronics	6	49997.53	299985.18
7	ORD100009	2025-12-05	CUST9622	Customer_224	35.0	Male	Kolkata	Laptop	Electronics	3	9488.83	28466.49
8	ORD100010	2025-11-21	CUST9770	Customer_494	41.0	Female	Mumbai	Book	Education	6	19488.23	116929.38
9	ORD100011	2025-04-16	CUST1312	Customer_40	30.0	Male	Kolkata	Mobile	Electronics	8	18024.34	144194.72


query = """
SELECT Quantity,
       Unit_Price,
       Total_Sales,
       Age
FROM apexplanet
"""

pd.read_sql(query, conn)

   
Quantity	Unit_Price	Total_Sales	Age
0	7	2829.77	19808.39	30.000000
1	5	27906.16	139530.80	63.000000
2	8	37491.06	299928.48	62.000000
3	9	28541.36	256872.24	65.000000
4	10	14036.59	140365.90	44.000000
...	...	...	...	...
995	9	35405.54	318649.86	61.000000
996	5	18454.65	92273.25	25.000000
997	9	12971.59	116744.31	62.000000
998	9	2879.01	25911.09	41.360204
999	9	22493.87	202444.83	58.000000




query = """
SELECT Customer_Name,
       COUNT(Order_ID) AS Orders,
       SUM(Total_Sales) AS Total_Spent,
       AVG(Total_Sales) AS Average_Order_Value
FROM apexplanet
GROUP BY Customer_Name
ORDER BY Total_Spent DESC;
"""
pd.read_sql(query, conn)
	Customer_Name	Orders	Total_Spent	Average_Order_Value
0	Customer_335	6	1684832.52	280805.420000
1	Customer_138	5	1305932.64	261186.528000
2	Customer_266	5	1269445.22	253889.044000
3	Customer_375	7	1196934.33	170990.618571
4	Customer_274	4	1060340.15	265085.037500
...	...	...	...	...
420	Customer_383	1	3992.85	3992.850000
421	Customer_421	1	3859.08	3859.080000
422	Customer_196	1	1495.14	1495.140000
423	Customer_38	1	1144.78	1144.780000
424	Customer_280	1	437.34	437.340000



query="""
SELECT City,
       SUM(Total_Sales) AS Revenue
FROM apexplanet
GROUP BY City
ORDER BY Revenue DESC
LIMIT 3;
"""
pd.read_sql(query, conn)

 
City	Revenue
0	Patna	20826584.43
1	Kolkata	18884349.57
2	Bengaluru	18773574.32


query="""SELECT Category,
       AVG(Total_Sales) AS Average_Sales
FROM apexplanet
GROUP BY Category;
"""
pd.read_sql(query, conn)


	Category	Average_Sales
0	Education	140627.468539
1	Electronics	143442.321186
2	Fashion	127153.178141
3	Furniture	135355.732579
4	Grocery	145305.302484

