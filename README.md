# rektcheck

## 0x095ea7b3  
There are some great existing tools out there for revoking allowances for a given ethereum address, and for these I am grateful.  
Many of us operate multiple ethereum accounts and when a contract gets exploited and SHTF it can be difficult to figure out which accounts could be at risk.  The intent of this tool is to allow you to quickly lookup whether any of the accounts under your control could be potentially vulnerable to a compromised contract  

I built this tool using an etherscan api endpoint, and therefore it is subject to rate limiting.  It is for this reason that I included the field to provide your own etherscan key so that you can use with out getting throttled due to traffic.  This is a a very simple one page app and no data is being collected whatsoever, you can verify for yourself by viewing the source code for this page.  If you don't have an etherscan api key, you can easily acquire one by creating an etherscan account.  But if you're really lazy and don't care about potentially getting rate-limited you can use mine: YDWWB5X3HQ9HPQQU24UWX4P4V4K8IESQW8  

## technical explanation
Using the etherscan endpoint `https://api.etherscan.io/api?module=account&action=txlist&address=[address]&startblock=0&endblock=99999999&sort=asc&apikey=[etherscanKey]`, the transaction history (last 10,000 txs) of each provided account address is searched for a tx input that begins with '0x095ea7b3' (denoting an approval) and has 'approvedSpender' of the tx set as the contract that you're worried about.  No external third party libraries are used and the only resources requested are from this page itself or etherscan.
