<h2 align="center"> FGProxy </h2>

<p align="center"><img src="https://raw.githubusercontent.com/Kr1s77/FgSurfing/main/log.png" 
        alt="Master"></p>



FGProxy  is an enterprise-level 4g agent program with automatic deployment. It is a more stable agent program than the 4g agent implemented by the Raspberry Pi. It discards the drawbacks of the Internet of Things card and uses a real 4g mobile phone card to build.

---

#### Create

>    `$ git clone https://github.com/Kr1s77/FgSurfing.git`
>
>   `$ cd FgSurfing/proxy`
>
>   `$ python3 api.py`
>
>   ```shell
>   >> [2021-07-15 14:22:32,522 INFO]  ->  Count: [1] Devices Found
>   >> [2021-07-15 14:22:32,522 INFO]  ->  Deploy device: FAXXXXXXX  1/1
>   ```

#### Overall structure

```
Clients -> Frp -> haproxy -> master -> Mobile slaver
```



##### Currently most of it has been completed
