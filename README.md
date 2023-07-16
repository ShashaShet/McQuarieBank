# I am making an assumption here that we have a csv file (sites.csv) which contains Urls of 10000 sites

# import contents of csv file 
$csvfile = Import-Csv -Path "sites.csv" 
# retrieve urls of 10000 sites under Url heading in csv file
$siteUrls = $csvfile.Url
# log in with your credentials 
$credential = get-credential
# Iterate through each url
foreach($siteUrl in $siteUrls)
{
   # connect to each site url
   Connect-PnPOnline -Url $siteUrl  -Credentials $credential 
   # Apply the site template
   Invoke-PnPSiteTemplate -Path "NewHRLifeSitetemplate.xml"
   

}
