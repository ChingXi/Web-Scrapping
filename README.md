# Web-Scrapping
Web Scrapping

url = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/stock.html"
html_data = requests.get(url).text

tables = soup.find_all('table')
for index,table in enumerate(tables):
    if ("Gamestop Quarterly Revenue" in str(table)):
        table_index = index

gme_revenue = pd.DataFrame(["Date", "Revenue"])
for row in tables[table_index].tbody.find_all("tr"):
    col = row.find_all("td")
    date = col[0].text
    revenue = col[1].text
    gme_revenue = tesla_revenue.append({"Date":date, "Revenue":revenue}, ignore_index=True)
