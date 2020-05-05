From 7f02102ccb465bc13fae70218065d3faabeb8fae Mon Sep 17 00:00:00 2001
From: Chandrika Deb <chandrikadeb7@gmail.com>
Date: Tue, 5 May 2020 10:08:13 +0530
Subject: [PATCH] Create patch file

---
 client3.py     | 12 ++++++++----
 client_test.py |  7 +++++--
 2 files changed, 13 insertions(+), 6 deletions(-)

diff --git a/client3.py b/client3.py
index f1771c3..220a692 100644
--- a/client3.py
+++ b/client3.py
@@ -35,25 +35,29 @@ def getDataPoint(quote):
 	stock = quote['stock']
 	bid_price = float(quote['top_bid']['price'])
 	ask_price = float(quote['top_ask']['price'])
-	price = bid_price
+	price = (bid_price + ask_price)/2
 	return stock, bid_price, ask_price, price
 
 def getRatio(price_a, price_b):
 	""" Get ratio of price_a and price_b """
 	""" ------------- Update this function ------------- """
 	""" Also create some unit tests for this function in client_test.py """
-	return 1
+	if(price_b==0):
+		return
+	return price_a/price_b
 
 # Main
 if __name__ == "__main__":
 
 	# Query the price once every N seconds.
-	for _ in iter(range(N)):
+	for _ in range(N):
 		quotes = json.loads(urllib.request.urlopen(QUERY.format(random.random())).read())
 
 		""" ----------- Update to get the ratio --------------- """
+		prices = {}
 		for quote in quotes:
 			stock, bid_price, ask_price, price = getDataPoint(quote)
+			prices[stock] = price
 			print ("Quoted %s at (bid:%s, ask:%s, price:%s)" % (stock, bid_price, ask_price, price))
 
-		print ("Ratio %s" % getRatio(price, price))
+		print ("Ratio %s" % getRatio(prices['ABC'], prices['DEF']))
diff --git a/client_test.py b/client_test.py
index af2bf26..bc510a0 100644
--- a/client_test.py
+++ b/client_test.py
@@ -1,5 +1,5 @@
 import unittest
-from client3 import getDataPoint
+from client3 import getDataPoint, getRatio
 
 class ClientTest(unittest.TestCase):
   def test_getDataPoint_calculatePrice(self):
@@ -8,6 +8,8 @@ class ClientTest(unittest.TestCase):
       {'top_ask': {'price': 121.68, 'size': 4}, 'timestamp': '2019-02-11 22:06:30.572453', 'top_bid': {'price': 117.87, 'size': 81}, 'id': '0.109974697771', 'stock': 'DEF'}
     ]
     """ ------------ Add the assertion below ------------ """
+    for quote in quotes:
+      self.assertEqual(getDataPoint(quote), (quote['stock'], quote['top_bid']['price'], quote['top_ask']['price'], (quote['top_bid']['price'] + quote['top_ask']['price'])/2))
 
   def test_getDataPoint_calculatePriceBidGreaterThanAsk(self):
     quotes = [
@@ -15,7 +17,8 @@ class ClientTest(unittest.TestCase):
       {'top_ask': {'price': 121.68, 'size': 4}, 'timestamp': '2019-02-11 22:06:30.572453', 'top_bid': {'price': 117.87, 'size': 81}, 'id': '0.109974697771', 'stock': 'DEF'}
     ]
     """ ------------ Add the assertion below ------------ """
-
+    for quote in quotes:
+      self.assertEqual(getDataPoint(quote), (quote['stock'], quote['top_bid']['price'], quote['top_ask']['price'], (quote['top_bid']['price'] + quote['top_ask']['price'])/2))
 
   """ ------------ Add more unit tests ------------ """
 
-- 
2.17.2 (Apple Git-113)

