---
title: Create, list, update and delete Microsoft Purview DevOps policies, so you can manage access to system health and performance counters.
description: Use Microsoft Purview DevOps policies to provision access to database system metadata, so IT operations personnel can monitor performance, health and audit security, while limiting the insider threat. This guide covers the basic operations.
author: inward-eye
ms.author: vlrodrig
ms.service: purview
ms.subservice: purview-data-policies
ms.topic: how-to
ms.date: 02/10/2023
ms.custom:
---
# Create, list, update and delete Microsoft Purview DevOps policies

[DevOps policies](concept-policies-devops.md) are a type of Microsoft Purview access policies. They allow you to manage access to system metadata on data sources that have been registered for *Data use management* in Microsoft Purview. These policies are configured directly from the Microsoft Purview governance portal, and after they are saved, they get automatically published and then enforced by the data source. Microsoft Purview policies only manage access for Azure AD principals.

This guide covers the configuration steps in Microsoft Purview to provision access to database system metadata using the DevOps policies actions *SQL Performance Monitoring* or *SQL Security Auditing*. It goes into detail on creating, listing, updating and deleting DevOps policies.

## Prerequisites
[!INCLUDE [Access policies generic pre-requisites](./includes/access-policies-prerequisites-generic.md)]

### Configuration
Before authoring policies in the Microsoft Purview policy portal, you'll need to configure the data sources so that they can enforce those policies.

1. Follow any policy-specific prerequisites for your source. Check the [Microsoft Purview supported data sources table](./microsoft-purview-connector-overview.md) and select the link in the **Access Policy** column for sources where access policies are available. Follow any steps listed in the Access policy or Prerequisites sections.
1. Register the data source in Microsoft Purview. Follow the **Prerequisites** and **Register** sections of the [source pages](./microsoft-purview-connector-overview.md) for your resources.
1. [Enable the "Data use management" toggle in the data source registration](how-to-enable-data-use-management.md). Additional permissions for this step are described in the linked document.


## Create a new DevOps policy
To create a new DevOps policy, ensure first that you have the Microsoft Purview Policy author role at **root collection level**. Check the section on managing Microsoft Purview role assignments in this [guide](./how-to-create-and-manage-collections.md#add-roles-and-restrict-access-through-collections).

1. Sign in to the [Microsoft Purview governance portal](https://web.purview.azure.com/resource/).

1. Navigate to the **Data policy** feature using the left side panel. Then select **DevOps policies**.

1. Select the **New Policy** button in the policy page. After that, the policy detail page will open.
![Screenshot shows to enter SQL DevOps policies to create.](./media/how-to-policies-devops-authoring-generic/enter-devops-policies-to-create.png)

1.  Select the **Data source type** and then one of the listed data sources under **Data source name**. Then click on **Select**. This will take you back to the New Policy experience
![Screenshot shows to select a data source for policy.](./media/how-to-policies-devops-authoring-generic/select-a-data-source.png)

1. Select one of two roles, *SQL Performance monitor* or *SQL Security auditor*. Then select **Add/remove subjects**. This will open the Subject window. Type the name of an Azure AD principal (user, group or service principal) in the **Select subjects** box. Note that Microsoft 365 groups are supported but updates to group membership take up to 1 hour to get reflected by Azure AD. Keep adding or removing subjects until you are satisfied. Select **Save**. This will take you back to the prior window.
![Screenshot shows to select role and subject for policy.](./media/how-to-policies-devops-authoring-generic/select-role-and-subjects.png)

1. Select **Save** to save the policy. A policy has been created and automatically published. Enforcement will start at the data source within 5 minutes.

## List DevOps policies
To update a DevOps policy, ensure first that you have one of the following Microsoft Purview roles at **root collection level**: Policy author, Data source admin, Data curator or Data reader. Check the section on managing Microsoft Purview role assignments in this [guide](./how-to-create-and-manage-collections.md#add-roles-and-restrict-access-through-collections).

1. Sign in to the [Microsoft Purview governance portal](https://web.purview.azure.com/resource/).

1. Navigate to the **Data policy** feature using the left side panel. Then select **DevOps policies**.

1. If any DevOps policies have been created they will be listed as shown in the following screenshot
![Screenshot shows to enter SQL DevOps policies to list.](./media/how-to-policies-devops-authoring-generic/enter-devops-policies-to-list.png)


## Update a DevOps policy
To update a DevOps policy, ensure first that you have the Microsoft Purview Policy author role at **root collection level**. Check the section on managing Microsoft Purview role assignments in this [guide](./how-to-create-and-manage-collections.md#add-roles-and-restrict-access-through-collections).

1. Sign in to the [Microsoft Purview governance portal](https://web.purview.azure.com/resource/).

1. Navigate to the **Data policy** feature using the left side panel. Then select **DevOps policies**.

1. Enter the policy detail for one of the policies by selecting it from its Data resource path as shown in the following screenshot
![Screenshot shows to enter SQL DevOps policies to update.](./media/how-to-policies-devops-authoring-generic/enter-devops-policies-to-update.png)

1. In the policy detail page, select **Edit**.

1. Continue same as with step 5 and 6 of the policy create.

## Delete a DevOps policy
To delete a DevOps policy, ensure first that you have the Microsoft Purview Policy author role at **root collection level**. Check the section on managing Microsoft Purview role assignments in this [guide](./how-to-create-and-manage-collections.md#add-roles-and-restrict-access-through-collections).

1. Sign in to the [Microsoft Purview governance portal](https://web.purview.azure.com/resource/).

1. Navigate to the **Data policy** feature using the left side panel. Then select **DevOps policies**.

1. Check one of the policies and then select **Delete** as shown in the following screenshot:
![Screenshot shows to enter SQL DevOps policies to delete.](./media/how-to-policies-devops-authoring-generic/enter-devops-policies-to-delete.png)

## Next steps
Check the blogs, videos and related docs
* Blog: [Microsoft Purview DevOps policies enter General Availability](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-purview-devops-policies-enter-ga-simplify-access/ba-p/3674057)
* Blog: [Microsoft Purview DevOps policies enable at scale access provisioning for IT operations](https://techcommunity.microsoft.com/t5/microsoft-purview-blog/microsoft-purview-devops-policies-enable-at-scale-access/ba-p/3604725)
* Video: [DevOps policies quick overview](https://aka.ms/Microsoft-Purview-DevOps-Policies-Video)
* Video: [DevOps policies deep dive](https://youtu.be/UvClpdIb-6g)
* Video: [Pre-requisite for policies: The "Data use management" option](https://youtu.be/v_lOzevLW-Q)
* Document: [Microsoft Purview DevOps policies on Azure Arc-enabled SQL Server](./how-to-policies-devops-arc-sql-server.md)
* Document: [Microsoft Purview DevOps policies on Azure SQL DB](./how-to-policies-devops-azure-sql-db.md)