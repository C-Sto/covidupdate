# covidupdate
a slackbot that updates current covid-19 numbers

Currently pulls data for Aus,NZ,US from three datasources (supposedly up-to-date sources):

- AU: https://www.health.gov.au/news/health-alerts/novel-coronavirus-2019-ncov-health-alert/coronavirus-covid-19-current-situation-and-case-numbers
- US: https://www.cdc.gov/coronavirus/2019-ncov/cases-updates/cases-in-us.html
- NZ: https://www.health.govt.nz/our-work/diseases-and-conditions/covid-19-novel-coronavirus/covid-19-current-cases

# Requires:
- golang
- a computer to run on
- a Slack bot token (should look similar to "xoxb-XXXXXX-XXXXXXXX-XXXXXXX")
- a slack channel and name
- the :remain_indoors: tag to be added to the slack as a custom emoji (use the supplied image file)

# Usage:

Add the bot to the slack and invite it to the target channel(s) (see https://api.slack.com/authentication/basics)

`cd /path/to/covidupdate`

`go get -u`

`go build covid.go`

`crontab -e # on the server you want it to run from`

Add an entry to run every 10 mins:

`*/10 * * * * /path/to/covid -key "xoxb-XXXXXX-XXXXXXXX-XXXXXXX" -channel covid-19 -file covidtable.csv`
(hint: replace the channel and key with your own details. file is less important; that's where covid will store and check data from)

# Screenshot of covideupdate doing its thang.

![coviduptate](covidupdate.png)

# Ack
@c-sto / `github.com/c-sto` for helping fix the AU data source after they switched it to websockets (lol)
