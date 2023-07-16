# I am making an assumption here that we have a csv file (sites.csv) which contains Urls of 10000 sites

$csvfile = Import-Csv -Path "sites.csv" 

$siteUrls = $csvfile.Url
$credential = get-credential
foreach($siteUrl in $siteUrls)
{
    Connect-PnPOnline -Url $siteUrl  -Credentials $credential 
    Invoke-PnPSiteTemplate -Path "NewHRLifeSitetemplate.xml"

}
