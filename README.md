##Here're some squid configuration lines on top of the default configuration lines

##Authentication lines

auth_param basic program /usr/lib64/squid/basic_ncsa_auth /etc/squid/users

auth_param basic children 5

auth_param basic realm Squid proxy-caching web server

auth_param basic credentialsttl 2 hours

acl auth_users proxy_auth REQUIRED

auth_param basic casesensitive off


##Limit the source hosts

acl hosts_allow src 64.157.241.2

acl hosts_allow src 123.113.84.82


##Allow lines

http_access allow auth_users hosts_allow

##Remove forwarder and squid tag

request_header_access Via deny all

request_header_access X-Forwarded-For deny all
