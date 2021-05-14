########################
# CREATE LIMIT ORDER
########################
# https://www.twitch.tv/crypto_bot_1mio
# Please Follow for Support
########################

import time, json, requests, hashlib, hmac

# ADD YOUR API_KEY, SECRET_KEY
a_key = "-----" 
s_key = "-----"


#--CONFIG-----------------------------------
# Trading Pair
tpair = "BTCUSDT"	

# Side
tside = "BUY"		

# Quantity of the main Asset, look to HP how many commas are allowed
amount = "0.00002"

# Price
price = "56000"
#-----------------------------------------


# Sync server time with pc-time
try:
	r = requests.get ("https://api.binance.com/api/v1/time", timeout=4)
except:
	print ("TIME SYNC FAIL\n" + r.text)
	

# Order Send
base_url = "https://api.binance.com/api/v3/order"
first = "?"
symbol = "symbol=" + tpair.upper()
side = "&side=" + tside.upper()
typee = "&type=LIMIT"
timeinforce = "&timeInForce=GTC"
amount = "&quantity=" + str(amount)
price = "&price=" + str(price)
time = "&timestamp=" + str((int("%.0f" % time.time()) * 1000) + int( r.json() ["serverTime"]) - int("%.0f" % (time.time() * 1000)))

query = symbol + side + typee + timeinforce + amount + price + time
signature = hmac.new(s_key.encode("utf-8"), query.encode("utf-8"), hashlib.sha256).hexdigest()
sign_end = "&signature=" + signature
url_rdy = base_url + first + query + sign_end
header = {'X-MBX-APIKEY' : a_key}


try:
	r = requests.post (url_rdy, headers=header, timeout=4)
	print ("\nREQUEST SEND OKAY\n" + r.text)

except:
	print ("\nREQUEST SEND FAIL\n" + r.text)
