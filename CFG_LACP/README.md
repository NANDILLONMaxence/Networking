# Guide d'Agrégation de Liens sur Switchs Cisco

## Introduction

L'agrégation de liens sur les équipements Cisco permet le regroupement de liens identiques pour former un seul lien logique. Cette pratique offre plusieurs avantages, notamment l'augmentation de la bande passante entre les équipements et la redondance en cas de défaillance d'un lien.

Le présent guide explique comment configurer l'agrégation de liens sur des switchs Cisco, en utilisant des exemples concrets.

## Schéma de l'Agrégation

Voici un schéma représentant un exemple d'agrégation de liens avec 2 switchs :

<img src= "https://github.com/NANDILLONMaxence/Networking/blob/main/CFG_LACP/screen/1-schema_agregat_liens.png" width="100%" />

## Configuration

<img src= "https://github.com/NANDILLONMaxence/Networking/blob/main/CFG_LACP/screen/2-ARCHI_TP_PO.png" width="100%" />

### Agrégat de 2 Liens (Port Channel 1)

#### Configuration de S2
```bash
interface GigabitEthernet1/0/47
channel-group 1 mode on
switchport mode trunk

interface GigabitEthernet1/0/48
channel-group 1 mode on
switchport mode trunk

interface Port-Channel1
switchport mode trunk
```

#### Configuration de S3
```bash
interface GigabitEthernet1/0/47
channel-group 1 mode on
switchport mode trunk

interface GigabitEthernet1/0/48
channel-group 1 mode on
switchport mode trunk

interface Port-Channel1
switchport mode trunk
```

Pour vérifier l'état de l'agrégat de 2 liens, utilisez les commandes suivantes :
```bash
show etherchannel summary
show interfaces Port-Channel1
```

### Agrégat de 3 Liens (Port Channel 2)

#### Configuration de S1
```bash
interface GigabitEthernet1/0/1
channel-group 2 mode on
switchport mode trunk

interface GigabitEthernet1/0/2
channel-group 2 mode on
switchport mode trunk

interface GigabitEthernet1/0/3
channel-group 2 mode on
switchport mode trunk

interface Port-Channel2
switchport mode trunk
```

#### Configuration de S2
```bash
interface GigabitEthernet1/0/1
channel-group 2 mode on
switchport mode trunk

interface GigabitEthernet1/0/2
channel-group 2 mode on
switchport mode trunk

interface GigabitEthernet1/0/3
channel-group 2 mode on
switchport mode trunk

interface Port-Channel2
switchport mode trunk
```

Pour vérifier l'état de l'agrégat de 3 liens, utilisez les commandes suivantes :
```bash
show etherchannel summary
show interfaces Port-Channel2
```

---

Ce document vous guide à travers les étapes de configuration de l'agrégation de liens sur des switchs Cisco, en fournissant des exemples de configurations pour des agrégats de 2 et 3 liens. Utilisez les commandes de vérification pour confirmer le bon fonctionnement de vos agrégats.

C'est tout ! Vous savez maintenant comment mettre en place l'agrégation de liens sur vos switchs Cisco.

---
