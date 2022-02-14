### Trust DEV Certificates

(can't remember if you need elevated/admin cmd to do that, try without first)

`dotnet dev-certs https --clean`
`dotnet dev-certs https --trust`

that will clean all previous dev-certs if you had any and regenerate a new one and put it in your cert store
(if one of the following point is missleading, either ask or ignore the line)


TLDR: that will only work locally
TLDR2: if you still have issue with postman, it means postman don't properly use the certificate from your computer, either restart postman, or check the settings
TLDR3: localhost only


certificate are
* stored only on the computer that you ran that command
* every time you run --trust it's a NEW (sort of random) ONE created
* generated only for https://localhost


meaning:
* if you try to do the request from another computer => won't work because it's not localhost
* even if you setup a local DNS to point to localhost => https://my-pc won't work
* "default setup" with container won't work => because "localhost" from a container is the container itself, => think that each container is like a separate computer on your network 
