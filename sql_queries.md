query = """
SELECT Product,
SUM(Sales) AS Revenue
FROM sales
GROUP BY Product
ORDER BY Revenue DESC
LIMIT 5
"""

pd.read_sql(query, conn)

	Product	   Revenue
0	Webcam	   517070.300538
1	Headphones 400160.820000
2	SSD	   382114.420000
3	Mouse	   327650.110000
4	Laptop	   306992.350000





query = """
SELECT COUNT(*) AS TotalOrders
FROM sales
"""

pd.read_sql(query, conn)

   TotalOrders
0	90




query = """
SELECT Product,
SUM(Profit) AS TotalProfit
FROM sales
GROUP BY Product
ORDER BY TotalProfit DESC
"""
pd.read_sql(query, conn)
        Product	   TotalProfit
0	Webcam	   88082.39
1	SSD	   85417.82
2	Headphones 66004.21
3	Laptop	   65343.05
4	Mouse	   58084.99
5	Monitor	   49703.97
6	Keyboard   45529.95
7	Printer	   10698.36




query="""SELECT [Customer Name],
SUM(Sales) AS TotalSales
FROM sales
GROUP BY [Customer Name]
ORDER BY TotalSales DESC
"""
pd.read_sql(query, conn)

  Customer Name	TotalSales
0	Rohit	303606.920538
1	Priya	299084.360000
2	Kiran	281994.620538
3	Pooja	276533.420000
4	Meera	262043.660000
5	Anjali	254687.530000
6	Sneha	232626.530000
7	Vikram	223981.710000
8	Aarav	201452.900000
9	Rahul	126204.230000





query="""SELECT AVG(Sales)
FROM sales
"""
pd.read_sql(query, conn)


AVG(Sales)
0	27357.954234
