University: [ITMO University](https://itmo.ru/ru/)
Faculty: [FICT](https://fict.itmo.ru)

Course: [Introduction in routing](https://github.com/itmo-ict-faculty/introduction-in-routing)

Year: 2023/2024

Group: K33212

Author: Petrov Dmitry Konstantinovich

Lab: Lab4

Date of create: 17.12.2023

Date of finished:

# Лабораторная работа № 4

## Цель работы

Изучить протоколы BGP, MPLS и правила организации L3VPN и VPLS.

## Ход работы

1. Составлена топология сети:
![graph](./pngs/graph.png)
```
name: lab4

mgmt:
  network: lab4
  ipv4_subnet: 172.20.20.0/24

topology:
  nodes:
    R01.SPB:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.11

    R01.HKI:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.12

    R01.LBN:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.13

    R01.LND:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.14

    R01.NY:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.15

    R01.SVL:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.16

    PC1:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.21

    PC2:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.22

    PC3:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.23

  links:
    - endpoints: ["R01.SPB:eth1","PC1:eth1"]
    - endpoints: ["R01.SPB:eth2","R01.HKI:eth1"]
    - endpoints: ["R01.HKI:eth2","R01.LND:eth1"]
    - endpoints: ["R01.HKI:eth3","R01.LBN:eth1"]
    - endpoints: ["R01.LBN:eth2","R01.LND:eth2"]
    - endpoints: ["R01.LND:eth3","R01.NY:eth1"]
    - endpoints: ["R01.NY:eth2","PC2:eth1"]
    - endpoints: ["R01.LBN:eth3","R01.SVL:eth1"]
    - endpoints: ["R01.SVL:eth2","PC3:eth1"]
```

Работа состоит из 2 частей
1 часть:
* Настроить iBGP RR Cluster.
* Настроить VRF на 3 роутерах.
* Настроить RD и RT на 3 роутерах.
* Настроить IP адреса в VRF.
* Проверить связность между VRF
* Настроить имена устройств, сменить логины и пароли.

2 часть:
* Разобрать VRF на 3 роутерах (или отвязать их от интерфейсов).
* Настроить VPLS на 3 роутерах.
* Настроить IP адресацию на PC1,2,3 в одной сети.
* Проверить связность.

2. 1 часть:
* R01.SPB
![spb](./pngs/SPB.png)
* R01.HKI
![hki](./pngs/HKI.png)
* R01.LBN
![lbn](./pngs/LBN.png)
* R01.LND
![lnd](./pngs/LND.png)
* R01.NY
![ny](./pngs/NY.png)
* R01.SVL
![svl](./pngs/SVL.png)
* PC1
![pc1](./pngs/PC1.png)
* PC2
![pc2](./pngs/PC2.png)
* PC3
![pc3](./pngs/PC3.png)

2. 2 часть работы
* R01.SPB
![spbp2](./pngs/SPBp2.png)
* R01.NY
![nyp2](./pngs/NYp2.png)
* R01.SVL
![svlp2](./pngs/SVLp2.png)
* PC1
![pc1p2](./pngs/PC1p2.png)
* PC2
![pc2p2](./pngs/PC2p2.png)
* PC3
![pc3p2](./pngs/PC3p2.png)

3. Результаты тестов
* Пинги
![spbtest](./pngs/SPBpingtest.png)
![lndtest](./pngs/LNDpingtest.png)
* bgppeer на роутере LBN
![lbnbgp](./pngs/LBNbgppeer.png)
* проверка связности VRF
![vrf](./pngs/vpftest.png)
* проверка связности пк
![pc1sv](./pngs/PC1pingtest.png)
![pc3sv](./pngs/PC3pingtest.png)

4. Вывод:
Выполнив данную работу я изучил протоколы BGP, MPLS и правила организации L3VPN и VPLS.