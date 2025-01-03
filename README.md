# web-scraper
import requests
from bs4 import BeautifulSoup

url = 'https://ngit-netra.teleuniv.in'
headers = {'User-Agent': 'Mozilla/5.0'}

response = requests.get(url, headers=headers)
if response.status_code == 200:
    soup = BeautifulSoup(response.content, 'html.parser')
    # Example: Extract all links
    links = soup.find_all('a')
    for link in links:
        print(link.get('href'))
else:
    print(f'Failed to retrieve the page. Status code: {response.status_code}')
