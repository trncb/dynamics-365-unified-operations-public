---
# required metadata

title: Guidance for how to set up dual-write
description: This topic describes the scenarios that are supported for dual-write setup.
author: RamaKrishnamoorthy
manager: AnnBe
ms.date: 10/12/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-01-06

---

# Guidance for how to set up dual-write

[!include [banner](../../includes/banner.md)]

[!include [preview-banner](../../includes/preview-banner.md)]

You can set up a dual-write connection between a Finance and Operations environment and a Common Data Service environment.

+ A **Finance and Operations environment** provides the underlying platform for **Finance and Operations apps** (for example, Microsoft Dynamics 365 Finance, Dynamics 365 Supply Chain Management, and Dynamics 365 Retail).
+ A **Common Data Service environment** provides the underlying platform for **customer engagement apps** (Dynamics 365 Sales, Dynamics 365 Customer Service, Dynamics 365 Field Service, Dynamics 365 Marketing, and Dynamics 365 Project Service Automation).

>[!IMPORTANT]
>Human Resources in Finance and Operations supports dual-write connections, but the Dynamics 365 Human Resources app doesn't.

The setup mechanism varies, depending on your subscription and the environment.

+ For new instances of Finance and Operations apps, the setup of a dual-write connection begins in Microsoft Dynamics Lifecycle Services (LCS). If you have a license for Power Platform, you will get a new Common Data Service environment if your tenant doesn't have one.
+ For existing instances Finance and Operations apps, the setup of a dual-write connection begins in the Finance and Operations environment.

Before you start dual-write on an entity, you can run an initial sync to handle existing data on both sides of Finance and Operations apps and customer engagement apps. You can skip the initial sync if you don't need to synchronize data between the two environments.

An initial sync lets you copy existing data from one app to another bidirectionally. There are several different setup scenarios depending on which environments you already have and what type of data is in the environments.

The following setup scenarios are supported:

+ [A new Finance and Operations app instance and a new customer engagement app instance](#new-new)
+ [A new Finance and Operations app instance and an existing customer engagement app instance](#new-existing)
+ [A new Finance and Operations app instance that has data and a new customer engagement app instance](#new-data-new)
+ [A new Finance and Operations app instance that has data and an existing customer engagement app instance](#new-data-existing)
+ [An existing Finance and Operations app instance and a new customer engagement app instance](#existing-new)
+ [An existing Finance and Operations app instance and an existing customer engagement app instance](#existing-existing)

## <a id="new-new"></a>A new Finance and Operations app instance and a new customer engagement app instance

To set up a dual-write connection between a new instance of a Finance and Operations app that has no data and a new instance of a customer engagement app, follow the steps in [Dual-write setup from Lifecycle Services](lcs-setup.md). When the connection setup is completed, the following actions occur automatically:

- A new, empty Finance and Operations environment is provisioned.
- A new, empty instance of a customer engagement app is provisioned, where the CRM prime solution is installed.
- A dual-write connection is established for DAT company data.
- Entity maps are enabled for live synchronization.

Both environments are then ready for live data synchronization.

## <a id="new-existing"></a>A new Finance and Operations app instance and an existing customer engagement app instance

To set up a dual-write connection between a new instance of a Finance and Operations app that has no data and an existing instance of a customer engagement app, follow the steps in [Dual-write setup from Lifecycle Services](lcs-setup.md). When the connection setup is completed, the following actions occur automatically:

- A new, empty Finance and Operations environment is provisioned.
- A dual-write connection is established for DAT company data.
- Entity maps are enabled for live synchronization.

Both environments are then ready for live data synchronization.

To sync the existing Common Data Service data to the Finance and Operations app, follow these steps.

1. Create a new company in the Finance and Operations app.
2. Add the company to the dual-write connection setup.
3. [Bootstrap](bootstrap-company-data.md) the Common Data Service data by using a three-letter International Organization for Standardization (ISO) company code.
4. Run the **Initial sync** functionality for the entities that you want to sync data for.

For an example and alternative approach, see [Example](#example).

## <a id="new-data-new"></a>A new Finance and Operations app instance that has data and a new customer engagement app instance

To set up a dual-write connection between a new instance of a Finance and Operations app that has data and a new instance of a customer engagement app, follow the steps in the [A new Finance and Operations app instance and a new customer engagement app instance](#new-new) section earlier in this topic. When the connection setup is completed, if you want to sync the data to the customer engagement app, follow these steps.

1. Open the Finance and Operations app from the LCS page, sign in, and then go to **Data Management \> Dual-write**.
2. Run the **Initial sync** functionality for the entities that you want to sync data for.

For an example and alternative approach, see [Example](#example).

## <a id="new-data-existing"></a>A new Finance and Operations app instance that has data and an existing customer engagement app instance

To set up a dual-write connection between a new instance of a Finance and Operations app that has data and an existing instance of a customer engagement app, follow the steps in the [A new Finance and Operations app instance and an existing customer engagement app instance](#new-existing) section earlier in this topic. When the connection setup is completed, if you want to sync the data to the customer engagement app, follow these steps.

1. Open the Finance and Operations app from the LCS page, sign in, and then go to **Data Management \> Dual-write**.
2. Run the **Initial sync** functionality for the entities that you want to sync data for.

To sync the existing Common Data Service data to the Finance and Operations app, follow these steps.

1. Create a new company in the Finance and Operations app.
2. Add the company to the dual-write connection setup.
3. [Bootstrap](bootstrap-company-data.md) the Common Data Service data by using a three-letter ISO company code.
4. Run the **Initial sync** functionality for the entities that you want to sync data for.

For an example and alternative approach, see [Example](#example).

## <a id="existing-new"></a>An existing Finance and Operations app instance and a new customer engagement app instance

The setup of a dual-write connection between an existing instance of a Finance and Operations app and a new instance of a customer engagement app occurs in the Finance and Operation environment.

1. [Set up the connection from the Finance and Operations app](enable-dual-write.md).
2. Run the **Initial sync** functionality for the entities that you want to sync data for.

For an example and alternative approach, see [Example](#example).

## <a id="existing-existing"></a>An existing Finance and Operations app instance and an existing customer engagement app instance

The setup of a dual-write connection between an existing instance of a Finance and Operations app and an existing instance of a customer engagement app  occurs in the Finance and Operation environment.

1. Set up the connection from the Finance and Operations app.
2. To sync the existing Common Data Service data to the Finance and Operations app, [bootstrap](bootstrap-company-data.md) the Common Data Service data by using a three-letter ISO company code.
3. Run the **Initial sync** functionality for the entities that you want to sync data for.

For an example and alternative approach, see [Example](#example).

## Example

For an example, see [Enabling the Customers V3—Contacts entity map](enable-entity-map.md#example-enabling-the-customers-v3contacts-entity-map)

For an alternative approach based on data volumes in each entity that need to run initial sync, see [Considerations for initial synchronization](initial-sync-guidance.md).
