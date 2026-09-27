# x402watch draft

Post 1
I probed every paid x402 API on the Coinbase Bazaar and x402scan, unpaid, and the first crawl found a listed endpoint charging ten times its declared price.

Post 2
An agent that pays per call should know the endpoint is up, the price is real, and roughly how long it takes, before it signs a payment. Nobody was checking. So x402watch checks every six hours.

Post 3
One unpaid request per endpoint with the listed method and example body. A healthy paid endpoint answers 402 with a PAYMENT-REQUIRED header, and the live price comes straight out of that header.

Post 4
Scored 0 to 100. Uptime is 60 points, median latency 15, declared price matching live price 15, listing completeness 10. The last 30 probes count, so a fix at the source shows up in the score.

Post 5
A listing is a seller's claim. Now there is a receipt.

https://github.com/ucsandman/x402watch
