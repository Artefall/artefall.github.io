---
layout: post
title:  "Designing network topologies"
date:   2021-06-04 11:43:40 +0200
---

What if you need to organize local network, for company or your SOHO? It’s quite easy to connect all your PC’s and other network devices to switch and finally connect switch to newly-installed router. But what if you need to implement more complicated network, for two-storied building? This task requires more competent approach. First of all, like in other fields of activity, you need to start with planing and schema, called topology in networking terms.

Network topology visualizes arrangement and connection of network devices, such as PC’s, switches, routers, access points, phones, printers, servers, etc.

Today I want to show you how to build such topologies on practice.

All you need is a Microsoft Visio — app for drawing diagrams, schemas and another vector graphics. Visio has comprehensive set of pictures, icons and symbols, that represents network devices. Let’s start.
Target

Let’s set a goal and conditions for our lesson:

    Design plan of distributor company building.
    Building must consist of two floors.
    Design network topology of distributor company building.

Refresh our knowledge about network devices

For people, who know nothing about networks, I will remind briefly about basic network devices: Router and Switch.

    Switch is a network device, that connects network devices by physical addresses (MAC). Works on the Data Link stage of OSI model.
    Router is a network device, that connects networks by IP addresses.

In short, switch connects devices, while router connects networks.
Symbols

First off all, you need to include set of symbols to draw your schema:

    Walls, Doors and Windows

To include it, follow next steps:

More shapes > Maps and Floors plans > Building plan > Walls, Doors and Windows

    Computers and Monitors

To include it, follow next steps:

More shapes > Network > Computers and Monitors

    Network and Peripherals

To include it, follow next steps:

More shapes > Network > Network and Peripherals
Draw building plan

Open your Microsoft Visio. Include symbols as described below. We have bare white list:

Let’s add some carcass. Add walls, doors, etc. Assign name to every room and add sizes to your building and rooms.

First floor:

Second floor:

Note: if room have no network devices, you are welcome not to specify it on the plan. So there is no toilets, kitchens, piano, strip bar, etc.

Let’s add network devices, PC’s, etc.

First floor:

Second floor:

Let me explain some basic conventions of network topology and plans design:

    Switch in every room must have at least one free port for future connections.
    If building have two floors, every floor must have floor-switch, that connects every room switch — this move leads to system stability and scalability.
    Every switch must be signed as on example:

Where:

F — number of floor.

N — Number of Switch.

P — amount of ports in switch.

Great! We have designed plan of building. It’s time to resume all network at topology.
Draw topology

So, topology represents connection between network devices (routers, switches, access points) and devices, that works with network (PCs, phones, printers, etc.). To connect devices on plan, just select “connector” tool in visio.

Topology designing have one requirement — topology must be presented in hierarchical structure.
Congratulations!

This would give you enough information to make you design your own network topology and plans for buildings.

Thanks for reading!

I will be grateful if you support me on Patreon or Boosty

Follow me on telegram: https://t.me/secretsupper (most part of content could be found exactly in telegram).

Follow me on twitter: https://twitter.com/MaksymovArtem
