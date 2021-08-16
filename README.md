<h2 align="center"> FGProxy </h2>

<p align="center"><img src="https://raw.githubusercontent.com/Kr1s77/FgSurfing/main/log.png" 
        alt="Master"></p>



FGProxy  is an enterprise-level 4g agent program with automatic deployment. It is a more stable agent program than the 4g agent implemented by the Raspberry Pi. It discards the drawbacks of the Internet of Things card and uses a real 4g mobile phone card to build.

---

#### Before You Begin
1. The mobile phone must use a mobile phone that can execute `adb root`, I use [Google Pixel](https://en.wikipedia.org/wiki/Pixel_(1st_generation))，My system is [lineageos](https://www.lineageos.org/) 
2. Before using this program, you need to confirm that your phone has been configured according to the link below [How-do-I-run-python-on-Android-devices](https://kr1s77.github.io/2021/7/12/How-do-I-run-python-on-Android-devices/)
3. Then you can execute the Fgproxy program. After the execution is completed, the port will be mapped to 30000, 30001, 30002... The number of ports is the number of devices 
4. After that, configure haproxy for load balancing [Haproxy](https://github.com/haproxy/haproxy)
5. Since the machine is in our local area, we need to do intranet penetration to forward the local haproxy load balancing port, here we need [FRP](https://github.com/fatedier/frp)

=======The above is the overall configuration process. After the configuration is completed, the frp exit is our proxy port, which can be used in the crawler. 

#### Create

>   ```shell
>   $ git clone https://github.com/Kr1s77/FgSurfing.git
>   $ cd FgSurfing/proxy
>   $ python3 api.py
>   >> [2021-07-15 14:22:32,522 INFO]  ->  Count: [1] Devices Found
>   >> [2021-07-15 14:22:32,522 INFO]  ->  Deploy device: FAXXXXXXX  1/1
>   ```

#### Overall structure
```python3
 import requests
 
 url = 'https://httpbin.org/ip'
 proxies = {
     'http': 'http://{host}:{port}',
     'https': 'https://{host}:{port}'
 }
 
 requests.get(url=url, proxies=proxies)

# The following logic is then triggered：
# Clients -> Frp -> Haproxy -> Master PC -> Mobile Slaver
"""
 +----------------------------+
 | CLIENT || CLIENT || CLIENT |  
 +-------------+--------------+
               |
               |
               v
 +-------------+--------------+
 |          FRP SERVER        |
 +-------------+--------------+
               |
               |
               v
 +-------------+--------------+
 |           HAPROXY          |
 +-------------+--------------+
               |
               |
               v
+--------------+--------------+
|                             |
|           FGPROXY           |
|                             |
+-----------------------------+
"""
```

##### HAPROXY STATUS 
<p align="center"><img src="https://raw.githubusercontent.com/Kr1s77/FgSurfing/main/haproxy.png" 
        alt="Master"></p>

##### Currently most of it has been completed
> Anyone is welcome to participate and improve
> one person can go fast, but a group of people can go further
