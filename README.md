# NatTypeTester
Channel | Status
-|-
CI | [![CI](https://github.com/HMBSbige/NatTypeTester/workflows/CI/badge.svg)](https://github.com/HMBSbige/NatTypeTester/actions)
Stun.Net | [![NuGet.org](https://img.shields.io/nuget/v/Stun.Net.svg?logo=nuget)](https://www.nuget.org/packages/Stun.Net/)

## RFC supports

- [x] [RFC 3489](https://datatracker.ietf.org/doc/html/rfc3489)
- [x] [RFC 5389](https://datatracker.ietf.org/doc/html/rfc5389)
- [x] [RFC 5769](https://datatracker.ietf.org/doc/html/rfc5769)
- [x] [RFC 5780](https://datatracker.ietf.org/doc/html/rfc5780)
- [ ] [RFC 7350](https://datatracker.ietf.org/doc/html/rfc7350)
- [ ] [RFC 7443](https://datatracker.ietf.org/doc/html/rfc7443)
- [ ] [RFC 7635](https://datatracker.ietf.org/doc/html/rfc7635)
- [ ] [RFC 8489](https://datatracker.ietf.org/doc/html/rfc8489)

## Internet Protocol

- [x] IPv4
- [x] IPv6

## Transmission Protocol

- [x] UDP
- [ ] TCP
- [ ] TLS-over-TCP
- [ ] DTLS-over-UDP

## Preview
![](pic/1.png)

## RFC3489
<details>

![](pic/RFC3489.png)
</details>

## RFC5389
### Binding Test
<details>
  <summary>Checking for UDP Connectivity with the STUN Server</summary>

![](pic/RFC5780_4.2.png)
</details>

### Mapping Behavior
<details>
  <summary>Determining NAT Mapping Behavior</summary>

![](pic/RFC5780_4.3.png)
</details>

### Filtering Behavior
<details>
  <summary>Determining NAT Filtering Behavior</summary>

![](pic/RFC5780_4.4.png)
</details>

### Combining Tests
<details>

![](pic/RFC5780_4.5.png)

</details>

## STUN Server
### Docker
```
docker pull hmbsbige/stunserver
docker run -d --restart=always --net=host --name=stunserver hmbsbige/stunserver --mode full --primaryinterface $IP1 --altinterface $IP2
```
NAT0: OpenInternet，没有经过NAT地址转换，公网IP
NAT1: Full Cone NAT，动态家宽可以达到最优的状态，外网设备可以主动发信息给NAT1网络内的设备。
NAT2: Address-Restricted Cone NAT，只有内网设备(地址:任意端口)主动发过信息给外网设备，外网设备才能主动连接NAT2的该设备的地址(地址:任意端口)
NAT3: Port-Restricted Cone NAT，只有内网设备(地址:指定端口)主动发过信息给外网设备，外网设备才能主动连接NAT3的该设备的地址(地址:指定端口)，限制为通信过的端口
NAT4: Symmetric NAT，只能和NAT0设备通讯
