# Three-Site Enterprise WAN with OSPF

## **Overview**
This project documents a three-site enterprise WAN (HQ and two branches) built with **single-area OSPFv2**, **VLSM** addressing, a **floating static backup route** and **PAT** for internet access. Failover time is measured with default and tuned OSPF timers.

## **Network Topology**
- **HQ:** 2 routers
- **Branch-A and Branch-B:** 1 router each
- **ISP:** 1 router with a loopback of 8.8.8.8, plus a second link for backup
- **Network Range:** 10.0.0.0/16, split with VLSM for LANs, WAN links and loopbacks

## **Project Objectives**
- Plan the addressing with **VLSM**
- Configure **single-area OSPFv2** with manual router IDs
- Advertise a default route from HQ
- Add a **floating static route** as an internet backup
- Configure **PAT** on the HQ edge
- Add **IPv6 dual-stack** to one branch
- Measure failover time with default and tuned timers

---

## **1. Addressing Plan**
1. **Draw the three-site topology**
2. **Allocate subnets with VLSM, largest first**
3. **Record LANs, WAN links and loopbacks in a table**

## Addressing Plan - Visual Guide

<!-- screenshots -->


## **2. OSPF Configuration**
1. **Set a router ID on every router**
2. **Enable OSPF on the LAN and WAN interfaces**
3. **Make LAN interfaces passive**
4. **Set the same reference bandwidth on every router**
5. **Set the WAN links to point-to-point**

## OSPF Configuration - Visual Guide

<!-- screenshots -->


## **3. Internet Access and Default Routing**
1. **Add a default route on HQ towards the ISP**
2. **Advertise it with default-information originate**
3. **Add a floating static route with AD 130 as a backup**
4. **Configure PAT for the internal subnets**

## Internet Access and Default Routing - Visual Guide

<!-- screenshots -->


## **4. IPv6 Dual-Stack**
1. **Address one branch with IPv6**
2. **Add static IPv6 routes**
3. **Test IPv6 connectivity across the WAN**

## IPv6 Dual-Stack - Visual Guide

<!-- screenshots -->


## **5. Failover Testing**
1. **Place a switch between two routers so the interfaces stay up**
2. **Shut the far switch port during a continuous ping**
3. **Count the lost replies with default timers**
4. **Tune hello and dead timers and repeat the test**

## Failover Testing - Visual Guide

<!-- screenshots -->


## **6. Fault Testing**
1. **Create an area or timer mismatch**
2. **Create an MTU mismatch and watch it stick in ExStart**
3. **Make a WAN interface passive**
4. **Duplicate a router ID**
5. **Reverse NAT inside and outside**

## Fault Testing - Visual Guide

<!-- screenshots -->


## **Project Outcomes & Key Results**
- **Dynamic Routing** – All three sites learn routes through OSPF
- **Backup Path** – Internet access survives the loss of the primary link
- **Measured Convergence** – Failover time compared between default and tuned timers
- **Troubleshooting Record** – Each fault documented with symptom and fix

## **Potential Next Steps**
- **Move to multi-area OSPF**
- **Add eBGP to two ISPs**
- **Add a site-to-site IPsec VPN**

---

This project is part of my **Networking and Infrastructure portfolio**. For any inquiries, reach out via **[LinkedIn](https://www.linkedin.com/in/kimutai-fredrick/)**.

**_Built and documented by Fredrick Kimutai._**
