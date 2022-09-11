API_ENDPOINT = 'https://discord.com/api/v8'
CLIENT_ID = '1018444778137997353'
CLIENT_SECRET = 'oSEX4LiRvYvK9oz9hmjCoUHPfK0swNec'
REDIRECT_URI = 'https://google.com'

def exchange_code(code):
  data = {
    'client_id': CLIENT_ID,
    'client_secret': CLIENT_SECRET,
    'grant_type': 'authorization_code',
    'code': code,
    'redirect_uri': REDIRECT_URI
  }
  headers = {
    'Content-Type': 'application/x-www-form-urlencoded'
  }
  r = requests.post('%s/oauth2/token' % API_ENDPOINT, data=data, headers=headers)
  r.raise_for_status()
  return r.json()

def add_to_guild(access_token, userID):
        url = f"{API_ENDPOINT}/guilds/962766466455859210/members/{userID}"

        botToken = "MTAxODQ0NDc3ODEzNzk5NzM1Mw.GHB_1T.-9qWe6_DVPg4_L1uki_tioajBu_xIpSlHW_QbM"
        data = {
        "access_token" : access_token,
    }
        headers = {
        "Authorization" : f"Bot {botToken}",
        'Content-Type': 'application/json'

    }
        response = requests.put(url=url, headers=headers, json=data)
        print(response.text)

code = exchange_code("gDlnnyVouLkCRqpVo0QCAtPMPiplqJ")["access_token"]
add_to_guild(code, "954652623355654224")
