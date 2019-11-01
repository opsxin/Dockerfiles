# aria2-ariang

## Quick run

```bash
docker run --name aria2-ariang -d -p 80:80 -p 6800:6800 -p 6881:6881 hins/aria2-ariang
```

## Change RPC Password

```bash
docker run --name aria2-ariang -d \
    -p 80:80 \
    -p 6800:6800 \
    -p 6881:6881 \
    -e ARIA2_PASSWD="888888" \
    hins/aria2-ariang
```

### Environment Variables

- ARIA2_PASSWD: RPC Password
- ~~ARIA2_BT_PORT: BT Port~~
- ~~ARIA2_DHT_PORT: DHT Port~~

## Instructions

1. nginx default page is autoindex page.
2. **the page url of ariang is ${domain}/aria2/ or ${IP}/aria2/.**

<br/>

>  [AriaNG](https://github.com/mayswind/AriaNg) 
