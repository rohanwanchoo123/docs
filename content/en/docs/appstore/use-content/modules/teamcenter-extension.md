---
title: "Teamcenter Extension"
url: /appstore/modules/teamcenter-extension/
description: "Describes Teamcenter Extension from the Mendix Marketplace. Teamcenter Extension facilitates a low-code approach to integrating with Teamcenter."
---

## 1 Introduction {#introduction}

The [Teamcenter Extension](https://marketplace.mendix.com/link/component/225544) is a Mendix Extension built using the Mendix Extensibility Framework to provide you with an effortless means to harness the capabilities of [Teamcenter Connector](https://marketplace.mendix.com/link/component/111627) for Mendix. Teamcenter Extension is layered atop the Teamcenter Connector.It provides a low-code experience by making it easier to visualize and access Teamcenter data model and automate creation of Mendix domain models and microflows.

### 1.1 Typical Use Cases {#usecases}

Teamcenter Extension offers a list of use cases for which domain models and microflows can be created. After you select a use case, it uses an import mapping approach similar to Mendix [import mapping](/refguide/import-mappings/). Here, Teamcenter Extension allows you to select data from the business model of your Teamcenter instance. Based on the selected use case, the import mapping and, for some use cases, additional configurations, Teamcenter Extension generates and updates the domain model for your integration and generates one or more ready-to-use microflows that you can drag and drop into your application logic.

Teamcenter Extension offers the following integration options:

* Get item revisions
* Get workspace objects
* Create item and item revision
* Update item and item revision
* Revise item revisions
* Get structures

### 1.2 License {#license}

Teamcenter Extension is free to download and use. You may, however, require a Teamcenter (Author or Consumer) license to connect to Teamcenter.

### 1.3 Prerequisites {#prerequisites}

The compatibility between Teamcenter Extension and Studio Pro is as follows:

* Teamcenter Extension V 1.0.0 is compatible with Studio Pro versions between 10.6.5 and 10.7.

* Teamcenter Extension V 2.0.0 is compatible with Studio Pro version 10.12.1 or higher.

{{% alert color="info" %}}Teamcenter Extension is not compatible with Studio Pro versions between 10.8 to 10.11. </br></br>If you use one of these Studio Pro versions, a possible workaround is to use Teamcenter Extension in one of the compatible versions of Studio Pro first, create necessary artifacts and then import them into your version. However, Mendix always recommends using the latest MTS or LTS Studio Pro version.{{% /alert %}}

### 1.4 Dependencies {#dependencies}

You must have these Marketplace modules installed:

* [Community Commons](https://marketplace.mendix.com/link/component/170): only needed for Teamcenter Extension V 1.0.0

* [Teamcenter Connector](https://marketplace.mendix.com/link/component/111627): needed for all versions of Teamcenter Extension

  The table below details the compatibility between Teamcenter Extension, Teamcenter Connector, and Studio Pro.

| Teamcenter Extension Version | Teamcenter Connector | Studio Pro Version |
| ------------- | ------------- | ------------- |
| 1.0.0  | 3.6.1, 3.6.0, 3.5.0  | 10.6.5 thru 10.7  |
| 2.0.0  | 2406  | 10.12.1 and above  |

### 1.5 Demo App {#demoapp}

To see Teamcenter Extension in action, download and play with the [Teamcenter Extension Sample App](https://marketplace.mendix.com/link/component/225910).

## 2 Installation {#installation}

Follow the instructions in [Using Marketplace Content](/appstore/use-content/) to import Teamcenter Extension into your app.

## 3 Usage

### 3.1 Actions

#### 3.1.1 Get Item Revisions from Teamcenter {#getitemrevision}

The `Get ItemRevision` action allows you to generate the domain model and microflow to search for and retrieve `ItemRevisions` or its specialization. The resulting microflow implements the saved query `Item Revision...` from Teamcenter.

#### 3.1.2 Get Workspace Objects {#getworkspaceobjects}

The `Get Workspace Objects` action allows you to configure and generate the domain model and microflow to search for and retrieve Workspace Objects or their specialization from Teamcenter. This action implements the saved query `General..` from Teamenter

#### 3.1.3 Create Item and Item Revision {#createitem-and-itemrevision}

The `Create Item and Item Revision` action allows you to configure and generate the domain model and microflow to create an Item with `ItemRevision` or its specializations in Teamcenter. The resulting microflow implements the `Create Object and Update Properties` actions from the Teamcenter Connector. With the `Create Object` action, the `Item` and `ItemRevision` get created in Teamcenter, setting the Teamcenter properties that need to be set upon creation. With the `Update Properties` action, the remaining properties are updated in Teamcenter.

#### 3.1.4 Update Item and Item Revision {#updateitem-and-itemrevision}

The `Update Item and Item Revision` action allows you to generate the domain model and microflow to update an `Item` with `ItemRevision` or their specializations in Teamcenter. The resulting microflows implements the `Update Properties` action from the Teamcenter Connector. 

#### 3.1.5 Revise Item Revision {#reviseitem-and-itemrevision}

The `Revise Item and Item Revision` action allows you to generate the domain model and microflow to revise an `ItemRevision` or its specializations in Teamcenter. The resulting microflow implements the `Revise Object and Update Properties` actions from the Teamcenter Connector. With the `Revise Object` action, a new `ItemRevision` is created, setting the Teamcenter properties that need to be set upon revising. With the `Update Properties` action, the remaining properties are updated in Teamcenter.

#### 3.1.6 Get Structures

The `Get Structures` action allows you to generate the domain model and microflows to configure a BOM window and retrieve structure data from Teamcenter. This feature supports the retrieval of structures with the following:

* `RevisionRule` (or default `RevisionRule`)
* `VariantRule`
* `BOMWindow` property flags

Depending on the configuration, microflows are generated to do the following:

* Create `BOMWindow` (implementing the `Create BOM Windows2` action from the Teamcenter Connector)
* Retrieve `RevisionRules` (implementing the `Get Revision Rules` action from the Teamcenter Connector)
* Retrieve `VariantRules` (implementing the `Get Variant Rule` action from the Teamcenter Connector)
* Expand a single `BOMLine` (implementing the `Expand One Level 2` action from the Teamcenter Connector)
* Expand all `BOMLines` (implementing the `Expand All Levels` action from the Teamcenter Connector)
* Close the `BOMWindow` (implementing the `Close BOM Window`s action from the Teamcenter Connector)
* Get the root `BOMLine` for a `BOMWindow`.

To work with structures, such as BOMs, you need to first create a BOM window in Teamcenter. One can retrieve the root BOM Line from the BOM window and from there start expanding the structure either line by line or with all BOM Lines at the same time. The BOM Lines define the structure (based on the configuration you passed when generating the BOM window). Each BOM Line is associated with a single `ItemRevision`.

This feature is designed specifically for generating microflows and domain models to retrieve and display simple BOM structures (unconfigured or configured). For other scenarios, consider alternative solutions. See the table below:

| Scenario                                                 | Suggested Solution             |
| -------------------------------------------------------- | ------------------------------ |
| Work with large or complex BOM structures                | Use Active Workspace           |
| Have performance concerns                                | Use Active Workspace           |
| Transfer an entire BOM from Teamcenter to another system | Use Active Integration Gateway |
| Compare BOMs from different systems                      | Use Active Integration Gateway |
| Author BOMs                                              | Use Active Workspace           |
| Create BOM configurations                                | Use Active Workspace           |

### 3.2 Landing Page {#homepage}

To open Teamcenter Extension in Studio Pro, go to **Extensions** > **Teamcenter Extension** > **Teamcenter Extension**. If you use Studio Pro versions 10.7 or lower, Teamcenter Extension is available under **View** > **Teamcenter Extension**.

{{% alert color="info" %}}
For details on the version dependencies between Studio Pro and Teamcenter Extension, see the [Prerequisites](#prerequisites) section.
{{% /alert %}}

The landing page has with three tabs: **Menu**, **History**, and **Settings**.

#### 3.2.1 Menu Tab

The **Menu** tab displays use cases or actions you can create artifacts for using Teamcenter Extension.

![image](https://github.com/user-attachments/assets/750110c7-c609-4899-a262-4b7f9ea2332a)

#### 3.2.2 History Tab

The **History** tab displays the history of all actions (also referred as integrations) carried out in Teamcenter Extension.

![image](https://github.com/user-attachments/assets/80c6f074-0eb1-4d1f-9859-f5f28a5026e4)

On the **History** tab, you can view details of each action, such as entities and microflows created, Teamcenter URL used to connect with, the preview of the import mapping, and much more. 

 You can also edit, duplicate or delete an action using the buttons in the upper-right corner:

* **Delete** – This deletes the selected action from the list. However, it does not delete the corresponding entities and microflows, since they may impact pages or other integrations.
* **Duplicate** – This allows you to create a new action based on an existing one. When you click **Duplicate**, it clones the selected action and takes you to the import mapping page, where you can modify your mapping and subsequently create new domain model and microflows. This operation does not modify any of existing actions.
* **Edit** – This allows you to modify an existing action and updating existing domain model and microflows. When you click **Edit**, it takes you to the import mapping page, where you can add or edit entities, attributes, and associations, subsequently updating the domain model and microflows.

It is not recommended to make specific adjustments to artifacts generated by Teamcenter Extension outside of Teamcenter Extension. Doing so may result in breaking the integration. Instead, you should make adjustments inside Teamcenter Extension using the **Delete**, **Duplicate** or **Edit** operations, wherever possible. Examples of adjustments that are not advisable outside Teamcenter Extension are as follows:
* Modifying the **CreateInput** and **CompoundCreateInput** entities generated from The **Create Item** action
* Modifying any entity generated from the **Revise Item Revision** action
* Deleting attributes or associations generated by Teamcenter Extension
* Deleting or editing microflows generated by Teamcenter Extension

However, you can make the following adjustments outside Teamcenter Extension:
* Adding attributes or associations
* Moving microflows
* Renaming microflows

If you select an item in the **Action** list, Teamcenter Extension performs a validation check to see if the Teamcenter objects, entities, and microflows still exist and are valid. The results are reported in the **Validation** section.

#### 3.2.3 Settings Tab

The **Settings** tab displays the Teamcenter configuration page. 

![image](https://github.com/user-attachments/assets/c424a3bc-c841-43bd-a32d-14340330961d)

On the **Settings** tab, you can provide your Teamcenter Instance details to connect to, while building your app and using Teamcenter Extension. Click **Edit** to open a panel to enter details. The certificate path should be relative to the app directly.

Teamcenter Extension supports both HTTP and HTTPS connections. Additionally, it supports certificates that have *.crt* and *.pfx* file extensions.

### 3.3 Import Mapping {#importmapping}

Clicking any one of the actions opens an empty [import mapping](/refguide/import-mappings/) page. Here you can define what data you want to retrieve from Teamcenter and how to handle this data in Mendix. Depending on the action, the import mapping page starts with one or multiple entities or objects to configure, one per business object that needs to be configured. 

During configuration, the import mapping page will build up a preview of the Mendix domain model involved in the integration. In addition, the import mapping page shows the corresponding business objects on the Teamcenter side. For this, Teamcenter Extension displays both the display names of the objects and their properties, references, relations, and the corresponding technical names, as they will end up in the Mendix domain model.

In Teamcenter Extension, the import mapping consists of the following steps:

1. Object mapping: As Teamcenter works with many layers of specializations of its business objects, in the import mapping page, you need to configure which object type you want to retrieve from Teamcenter and what Mendix objects need to be created, when retrieving these business objects. This is called object mapping.
2. Selection of properties, references, and relations: Configure  which properties, references, and relations you want to retrieve from Teamcenter and include in your Mendix model .

{{< figure src="/attachments/appstore/modules/teamcenter-extension/domain-model.png" max-width=80% >}}

#### 3.3.1 Object Mapping {#objectmapping}

Clicking any one of the empty boxes in the import mapping page opens the object mapping dialog. On the left side of the dialog, a tree with all relevant business objects available from the configured Teamcenter instance is displayed. If you have created any custom business objects in Teamcenter BMIDE, those objects will be shown as well. The right side shows a tree of all relevant entities in your Mendix app.

The relevant objects and entities are dependent on the actions you are configuring. For example, for the action to get `ItemRevisions` from Teamcenter, the Teamcenter tree has an `ItemRevision` as its root object. That means that, for this action, you can only select `ItemRevisions` or its specializations. Similarly, in this example, the Mendix tree has the `TcConnector.ItemRevision` entity as its root entity.

{{< figure src="/attachments/appstore/modules/teamcenter-extension/select-objects.png" >}}

When retrieving a tree of objects, relevance can also be based on the type of the relation or reference. When working with typed relations o references, the type of Teamcenter business object is dictated by the relation or reference. By limiting the list of Teamcenter objects and Mendix entities to those that are relevant, Teamcenter Extension guides you to select Teamcenter business objects that make sense in the context of the action you want to perform.

To configure which type of Teamcenter business object you are interested in and what type of Mendix entities this should be mapped to, select a business object in the Teamcenter tree on the left side and an entity on the Mendix tree on the right side and click **OK**. 

It is also possible to create new entities for your integrations. This new entity needs to be a specialization of the root entity in the Mendix tree or one of its specializations. When you want to use a new entity, click your generalization of choice, click the **Create new specialization of selected entity** check box and provide an entity name. Once finishing the configuration for the actions, Teamcenter Extension will create a new entity with the given name and the selected entity as its generalization. You can also reuse or create the specialization of the generated entities in subsequent actions.

{{< figure src="/attachments/appstore/modules/teamcenter-extension/new-entity.png" >}}

Once you click **OK**, you will return to the import mapping tab with a sidebar open for you to configure which Teamcenter properties, references, and relations to include when retrieving data for this business object.

#### 3.3.2 Teamcenter Properties, References, and Relations {#tcprop}

In the import mapping sidebar, you can configure which Teamcenter properties, references, and relations to include when retrieving data from Teamcenter. The import mapping sidebar is launched automatically after the completion of object mapping. When you are on the import mapping page and the sidebar is closed, you can double-click a previously configured entity to open the sidebar for that entity.

The sidebar shows all properties, references, and relations for the configured Teamcenter object. Depending on the use case, each one of them is accompanied with check boxes for reading ({{% icon name="view" %}}) and writing ({{% icon name="pencil" %}}) for you to configure what to include when retrieving data from or creating data in Teamcenter.

You often see that check boxes are selected by default or grayed out. In general, the following rules apply:

1. Properties that are already available on the Mendix entity or one of its generalizations are selected by default and cannot be unchecked.
2. Properties, references, and relations for Marketplace entities are disabled by default, as it is not good practice to change Mendix marketplace content.

As an example, if a check box for reading ({{% icon name="view" %}}) is selected and grayed out, it means that property already exists as an attribute on the selected object or one of its generalizations. Similarly, if a check box for writing ({{% icon name="pencil" %}}) is selected and grayed out, it means the property is required during creation or revision of the selected object.

{{< figure src="/attachments/appstore/modules/teamcenter-extension/attributes-associations.png" max-width=60% >}}

You can select and deselect the properties, references, and relations depending on the data you need from Teamcenter. When you select a reference or relation, a new placeholder entity will be added to the object mapping tree. You will need to perform the import mapping for these referenced or related objects in a subsequent step (business object mapping and selection of Teamcenter properties, references, and relations).

### 3.4 Microflows and Domain Model

Once you finished import mapping, click **Generate** to create microflows for the selected use case and its corresponding domain model. These artifacts can be used in your app logic.

{{< figure src="/attachments/appstore/modules/teamcenter-extension/microflow.png" >}}
