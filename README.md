# aria2-ariang

## Quick run

```bash
docker run --name aria2-ariang -d -p 80:80 -p 6800:6800 -p 12345:12345 hins/aria2-ariang
```

## Other ways

```bash
docker run --name aria2-ariang -d \
    -p 80:80 \
    -p 6800:6800 \
    -p 1234:1234 \
    -p 2345:2345 \
    -e ARIA2_PASSWD="888888" \
    -e ARIA2_BT_PORT="1234" \
    -e ARIA2_DHT_PORT="2345" \
    hins/aria2-ariang
```

### Environment Variables

- ARIA2_PASSWD: RPC password
- ARIA2_BT_PORT: BT port
- ARIA2_DHT_PORT: DHT port

## Instructions

1. nginx default page is autoindex page.
2. the page url of ariang is  ${domain}/aria2/ or ${IP}/aria2/.

<br/>

>  [AriaNG](https://github.com/mayswind/AriaNg) 
