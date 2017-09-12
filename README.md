# IT Support engineer Questions


## How to submit the answers

1. Create a GitHub Account
1. Git Clone this repository to your local machine
1. Remove the current `origin` remote (`git remote remove origin`)
1. Create a new repository under your GitHub account (do **NOT** fork this repository)
1. Follow the instructions to `push an existing repository from the command line...`
1. Create a branch called `add_answers` on your local machine
1. Add answers to this Document (using a simple Text editor), commit your answers to the `add_answers` branch
1. Push your `add_answers` branch to your personal remote `origin`
1. Send a notification to your contact at Honestbee with a link to your repository

If any of the steps above is unclear, please try GitHub user guides first, then ask your contact at Honestbee to clarify. 

The method of submission is part of the test (usage of Git) - but we won't use `forks` or `pull requests`. 

## Questions

1.  A vendor is trying to connect to a server we publicly expose (assume we are not using VPN). When asked for his public IP from which he will be connecting, the vendor provides us with the following IP `192.168.0.100`, what should be our next steps? 

    1.  Include questions we may need to ask to get additional information to ensure this vendor will be able to connect over the public internet to our server. __Note that this vendor is not in our LAN, nor on a VPN with us__.

        > Add follow up Questions here as a bulleted list and add an explanation why you ask each question (what do you expect to receive back)

        1.  Example Follow Up Question 1
            Explanation for Example Follow Up Question 1
            
            192.168.0.100 is still the private IP address in the vendor company’s network.
            I will ask the vendor to check with their internet service provider to get the public IP address and default gateway.
                    
        1.  Example Follow Up Question 2
            Explanation for Example Follow Up Question 2
            
            I will ask the vendor to confirm if their public IP is fixed or not. It is hard to permit with dynimic IP addresses.
            Once we get the public ip & gateway, we can setup a tunnel in our firewall to allow the traffic from that public ip
            the vendor is able to connect to our server.
            


    1.  Write a PowerShell command (assume Windows 2012 R2) to add a new firewall rule on a single server, allowing incoming connections on port `3389` for `TCP` protocol __limited to the public IP of the vendor only__ (assuming we have the public IP of the vendor)


    Get-NetFirewallRule -DisplayName '*Remote Desktop*' | Set-NetFirewallRule -Action Allow
    Set-NetFirewallRule -Name RemoteDesktop-UserMode-In-TCP -RemoteAddress "192.168.0.100"
    

1.  How do you list all Computers in an Active Directory Domain using Powershell (output DNSHostname in a table format, no need for `filters` or `SearchBase`)

    
    Get-ADComputer -Filter * | Format-Table Name
    

1.  What could possible troubleshoot tests be for the following output on a macOS machine. 
    
    For each step, mention what would be your next step

    ```bash
    $ ping microsoft.com
    PING microsoft.com (23.100.122.175): 56 data bytes
    Request timeout for icmp_seq 0
    Request timeout for icmp_seq 1
    ...
    ```

    Notes:

    -   Local machines in the same network can still be pinged by IP
    
    1. Intract Net works fine as mcahines are still pingalbe within the network
    2. Unable to ping microsoft.com, need to check if this machine can access other web pages
       a) if can access other web pages, will try to create a new network location see if it helps
          or clear the network related .plist file (last step)
       b) if cant access other web pages, will try ping cmd again on another machine
          -if it works on the other machine, then it is a machine issue, same troubleshooting steps as a)
          -if it doesn't work on the other machine, then it maybe a network issue or a DNS server issue.
    3. Network issue, router unable to communicate with public network
          need to check whether it's a hardware issue or it's a service provider issue 
    4. DNS server issue, unable to resolve DNS request, need to check if the server is still responsible.
          If can get connection to the DNS server, try to check the dns settings and clear the cache.

Thank you for your time.
