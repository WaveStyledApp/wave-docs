# Proxy research

Notes about work done on August 8/25th 2022. Began looking at proxies

## Socks5
- Thought this would be a good path to start with. Turns out using a socks5 proxy is just a singular VPN without the encrpytion. I was under the assumption that it was a rotating ip proxy. Did a minor implementation of this and quickly realized the IP was static 
## Ip rotation
- https://github.com/Ge0rg3/requests-ip-rotator
    - Uses AWS gateway
        - https://aws.amazon.com/api-gateway/
- Essentially uses an AWS service that has a large pool of IPs and every request made from a session of this thing has a different IP. 
## Next Steps 
- Create admin IAM creds and a secrent+public key to use. 
- Try and implement this.
