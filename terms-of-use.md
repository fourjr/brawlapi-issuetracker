# Terms of Use

This is effective as of 4 March 2019.

By allowing your script or project (your "program") to interact with [BrawlAPI](https://brawlapi.cf/api) (the "API"), you agree to the following terms:

1. You must adhere to the [Supercell Fan Content Policy](https://supercell.com/en/fan-content-policy/)
2. You must adhere to the [Supercell Terms of Service](https://supercell.com/en/terms-of-service/)
3. Your program has to be unique and not a copy of someone else's work. 
4. Your program must not have any malicious intent.
5. Your program cannot state that it is affiliated or endorsed by the authors/contributors of the API. 
6. No circumventing or bypassing ratelimits.
7. You must not leave the API Discord Server.
8. You are not allowed to purposely spam the API.
9. The authorisation token your program uses has to be from your main account *only*.

Any action done under your token is your fault. If your token gets leaked and someone else abuses it, the responsibility still lies on you.

The API authors/contributors have the right to revoke your access to the API permanently or temporarily without any prior notice. 

# Best Practices
- Avoid sending many requests at a time, but rather include a latency in between requests
```markdown
# Good
> request
> wait
> request
> wait

# Bad
> request
> request
> request
> wait
> request
> request
```
- Do not continously request the API when you get a "error response" (status code > 500). Include a latency (i.e. 1 minute before requesting again)
    - API recovers at most 5 minutes after a maintenance break
    - Check for maintenance breaks! `maintenance` key would be `true` in 503 responses
- Cache your data. 
    - API has a **3 minute TTL cache** so requesting the same data within 3 minutes of the previous request wouldn't be effective. It would only take up server load and slow down other requests.
- Include a [User-Agent](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/User-Agent) header.
- Use [gzip](https://www.gzip.org/) compression
    - This cuts latency into almost half!
    - Include the `Accept-Encoding: gzip` header.
