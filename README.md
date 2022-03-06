# Shark-Tank-India-Entrepreneurs-
•	First import pandas, selenium and beautiful soup packages.
•	we need load URL by URL = ‘'https://www.serialupdates.me/shark-tank-india-investors-names-sony-tv-new-show-entrepreneurs-list/'’
•	For a static webpage we need to use requests() to request the html code of the webpage using html requests like html = requests.get(url).text.
•	Get the html code of the page using soup = BeautifulSoup(html, 'html.parser')
•	Let’s scrape the table row wise.
•	Let’s scrape the top row i.e., “Sr No.”, “Entrepreneur Name”, “From”, “Business” and so on
•	To know the div and class we need to use inspect mode right clicking on the mouse
•	From the html code  our desired top row of the table contains div : ‘figure’ and class: ‘wp-block-table is-style-stripes’ 
•	soup.select('figure.wp-block-table.is-style-stripes')[1] – using this we’re are locating the required table. 
•	Scrape ‘th’ cell using .text.strip() function: soup.select('figure.wp-block-table.is-style-stripes')[1].find_all('th')[0].text.strip() and iterate to get all the ‘th’ cells by [i.text.strip() for i in soup.select('figure.wp-block-table.is-style-stripes')[1].find_all('th')]
•	Scrape the data row wise using ‘tbody’ and ‘tr’ soup.select('figure.wp-block-table.is-style-stripes')[1].tbody.find_all('tr')[0].text.strip()
•	Iterate the above ‘tr’ cell to get all the row values: or r in soup.select('figure.wp-block-table.is-style-stripes')[1].tbody.find_all('tr'):
data.append([i for i in r.find_all('td')])
•	Define a function named SharkTank() to combine the top row and other value rows in a dataframe using pd.DataFrame
•	Import the function dataframe to a csv file using .to_csv(‘file name’)
