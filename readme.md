# IP Tickets Bot
> Please go through the [usecase description](https://www.youtube.com/watch?v=zjChX-Y0fPk)
---
[IP Tickets Website](https://botsdna.com/IPTicketingTool/)

## In this project, we perform the following activities
1. open browser with **IP Tickets Website**
    1. extract tabular data under **tickets** tab to **dt_Tickets** DataTable
    1. extract tabular data under **network** tab to **dt_Network** DataTable
    1.  extract tabular data under **location** tab to **dt_Location** DataTable
    1. join **dt_Network** & **dt_Location** DataTables and save it as **dt_NetworkAndLocation** DataTable

1. loop through each row in **dt_Tickets** DataTable
    1. get **TickeNo** and **Requester** details from each row using **matches** 
    activity
    1. get **TicketURL** by performing string concatenation between **Ticket Website** and **TicketNo**
    1.  invoke **Donwload_Zip_File_And_UnZip** workflow
        1.Download **IP Address** file
        1. unzip donwloaded zip file 
        1. send extracted zip file path to main workflow
    1. read extracted zip file and save it to **IPAddressFile**
    1. get **IpAddress** from **IPAddressFile** using **matches** activity
    1. loop through each **IPAddress**
        1. filter **dt_NetworkAndLocation** to get a single record and save it to **FilteredDT**
        1. grab details like **IP Owner, Provider, ASN, City, Postal Code, Country, Coordinates**
        1. Prepare Message body
    1. open browser with **IP Tickets Website** navigate to **find people** page
    1. enter requester name in search bar
    1. select the requester
    1. enter message in input text area
    1. click submit button
    1. click back button

1. close browser
1. done

### Key takeaways
- **Join DataTables**
- **Matches** activity for string parsing using **Regular Expression**
- unzip file using **extract/unzip files** activity
- download files using **HTTP request** activity
- **move files** 
