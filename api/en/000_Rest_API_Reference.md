# Personium API Reference

Welcome to the Personium API Reference.  This reference describes technical detailed specifications related to all of the APIs provided by Personium.

## Unit Level API
The Unit Level API's belong to the unit that hosts a group of cells and provide functions such as creating cells or managing a group of created cells. In principle, Unit Level API's cannot be accessed using the access tokens issued by normal cells and can only be accessed with Unit User Tokens.

#### Unit Root URL

```
https://{UnitFQDN}/
```

#### Unit Control Objects
Most of the Unit Level API's are implemented in the form of Unit Control Objects. 
Since they conform with the OData standard, their manipulation can be made in 
a RESTful and standardized manner.

|Cell|Operations|
|:--|:--|
|Basic Operations|[Create](100_Create_Cell.md) &nbsp; &nbsp; [Retrieve List](101_List_Cell.md) &nbsp; &nbsp; [Retrieve](102_Get_Cell.md) &nbsp; &nbsp; [Update](103_Update_Cell.md) &nbsp; &nbsp; [Delete](104_Delete_Cell.md)|

#### Other API's

*  [Cell Recursive Deletion](105_Cell_Recursive_Delete.md)

## Cell Level API

Cell Level API's are deployed under the following root URL.

#### Cell Root URL
```
https://{UnitFQDN}/{CellName}/
```

Cell Level API's provides the following features:

*  User and application Authentication
*  Access control
*  Networking Cells
*  Box creation and management
*  Message exchange between Cells
*  Event processing
*  Other features

Most of these functions are implemented in the form of Cell Control Objects that can be operated with the OData protocol, which is a standard for performing relational data manipulation based on REST.


### User and application Authentication

#### Authentication

* [OAuth2.0 Authorization Endpoint](292_OAuth2_Authorization_Endpoint.md)
* [OAuth2.0 Token Endpoint](293_OAuth2_Token_Endpoint.md)
* [Change Password](294_Password_Change.md)

#### Account (Cell Control Object)

|Account|Operations|
|:--|:--|
|Basic Operations|[Create](212_Create_Account.md) &nbsp; &nbsp; [Retrieve](213_Retrieve_Account.md) &nbsp; &nbsp; [Retrieve List](214_Search_Account.md) &nbsp; &nbsp; [Update](215_Update_Account.md) &nbsp; &nbsp; [Delete](216_Delete_Account.md)|
|&nbsp; &nbsp; Linking with other objects|[Link](217_Register_Account_links.md) &nbsp; &nbsp; [Unlink](220_Delete_Account_links.md) &nbsp; &nbsp; [List Links](218_Acquire_Account_links_List.md) <br> There is no link update. If you want to update, delete it and recreate it.|
|&nbsp; &nbsp; Bound Object Manipulation|[Create](221_Register_Account_Navigation_Property.md) &nbsp; &nbsp; [Retrieve](222_Acquire_Account_Navigation_Property.md)|

### Access control

Personium Cells employ Role-Based Access Control. A role can be defined in the form of Cell Control Object "Role".
Cell-level ACL can be configured with the following API, where multiple pairs of role and granted privileges can be defined.

* [Cell-level ACL Configuralion](289_Cell_ACL.md)

Configured ACL can be retrieved together with other properties, by sending regular WebDAV PROPFIND request to the root URL of the Cell. 

* [Retrieve Properties](290_Cell_Get_Property.md)
* [Change Properties](291_Cell_Change_Property.md)


#### Cell Control Object

|Role|Operations|
|:--|:--|
|Basic Operations|[Create](201_Create_Role.md) &nbsp; &nbsp; [Retrieve](203_Search_Role.md) &nbsp; &nbsp; [Retrieve List](202_Retrieve_Role.md) &nbsp; &nbsp; [Update](204_Update_Role.md) &nbsp; &nbsp; [Delete](205_Delete_Role.md)|
|&nbsp; &nbsp; Linking with other objects|[Link](206_Create_Role_links.md) &nbsp; &nbsp; [Unlink](209_Delete_Role_links.md) &nbsp; &nbsp; [List Links](207_List_Role_links.md) <br> There is no link update. If you want to update, delete it and recreate it.|
|&nbsp; &nbsp; Bound Object Manipulation|[Create](210_Register_Role_Using_NavProp.md) &nbsp; &nbsp; [Retrieve](211_List_Using_Role_NavProp.md)|


### Networking Cells

#### External Cell (Cell Control Object)

|ExtCell|Operations|
|:--|:--|
|Basic Operations|[Create](223_Create_External_Cell.md) &nbsp; &nbsp; [Retrieve](225_Get_External_Cell.md) &nbsp; &nbsp; [Retrieve List](224_List_External_Cell.md) &nbsp; &nbsp; [Update](226_Update_External_Cell.md) &nbsp; &nbsp; [Delete](227_Delete_External_Cell.md)|
|&nbsp; &nbsp; Linking with other objects|[Link](228_Register_External_Cell_links.md) &nbsp; &nbsp; [Unlink](231_Delete_External_Cell_links.md) &nbsp; &nbsp; [List Links](229_List_External_Cell_links.md) <br> There is no link update. If you want to update, delete it and recreate it.|
|&nbsp; &nbsp; Bound Object Manipulation|[Create](232_Register_External_Cell_Using_NavProp.md) &nbsp; &nbsp; [Retrieve List](233_List_External_Cell_NavProp.md)|

#### Relation (Cell Control Object)

|Relation|Operations|
|:--|:--|
|Basic Operations|[Create](234_Create_Relation.md) &nbsp; &nbsp; [Retrieve](236_Retrieve_Relation.md) &nbsp; &nbsp; [Retrieve List](235_List_Relation.md) &nbsp; &nbsp; [Update](237_Update_Relation.md) &nbsp; &nbsp; [Delete](238_Delete_Relation.md)|
|&nbsp; &nbsp; Linking with other objects|[Link](239_Register_Relation_links.md) &nbsp; &nbsp; [Unlink](242_Delete_Relation_links.md) &nbsp; &nbsp; [List Links](240_List_Relation_links.md) <br> There is no link update. If you want to update, delete it and recreate it.|
|&nbsp; &nbsp; Bound Object Manipulation|[Create](243_Register_Using_Relation_NavProp.md) &nbsp; &nbsp; [Retrieve List](244_List_Using_Relation_NavProp.md)|


#### ExtRole (Cell Control Object)

|ExtRole|Operations|
|:--|:--|
|Basic Operations|[Create](245_Create_External_Role.md) &nbsp; &nbsp; [Retrieve](247_Get_External_Role.md) &nbsp; &nbsp; [Retrieve List](246_List_External_Role.md) &nbsp; &nbsp; [Update](248_Update_External_Role.md) &nbsp; &nbsp; [Delete](249_Delete_External_Role.md)|
|&nbsp; &nbsp; Linking with other objects|[Link](250_Register_External_Role_links.md) &nbsp; &nbsp; [Unlink](253_Delete_External_Role_links.md) &nbsp; &nbsp; [List Links](251_Retrieve_External_Role_links.md) <br> There is no link update. If you want to update, delete it and recreate it.|
|&nbsp; &nbsp; Bound Object Manipulation|[Create](254_Register_Using_Role_NavProp.md) &nbsp; &nbsp; [Retrieve List](255_List_External_Role_NavProp.md)|

### Box creation and management inside the Cell

* [Install Box](302_Box_Installation.md)
* [Retrieve Box Meta Data](303_Progress_of_Bar_File_Installation.md)
* [Retrieve URL](304_Get_Box_URL.md)
* [Recursive Delete](295_Box_Recursive_Delete.md)

#### Box (Cell Control Object)

|Box|Operations|
|:--|:--|
|Basic Operations|[Create](256_Create_Box.md) &nbsp; &nbsp; [Retrieve](258_Retrieve_Box.md) &nbsp; &nbsp; [Retrieve List](257_Search_Box.md) &nbsp; &nbsp; [Update](259_Update_Box.md) &nbsp; &nbsp; [Delete](260_Delete_Box.md)|
|&nbsp; &nbsp; Linking with other objects|[Link](261_Register_Box_links.md) &nbsp; &nbsp; [Unlink](264_Delete_Box_links.md) &nbsp; &nbsp; [List Links](262_List_Box_links.md) <br> There is no link update. If you want to update, delete it and recreate it.|
|&nbsp; &nbsp; Bound Object Manipulation|[Create](265_Register_Using_Box_NavProp.md) &nbsp; &nbsp; [Retrieve](266_List_Box_NavProp.md)|

### Message Exchange between Cells

#### Message Manipulation

* [Send a message](271_Send_Message.md)
* [Change Status](267_Received_Message_Approval.md) (Approve / Decline, etc.)

|Cell Control Object|Operations|
|:--|:--|
|**Sent Message**|[Retrieve](272_Retrieve_Sent_Message.md) &nbsp; &nbsp; [Retrieve List](273_List_Sent_Messages.md) &nbsp; &nbsp; [Delete](274_Delete_Sent_Message.md)|
|**Received Message**|[Retrieve](269_Get_Received_Message.md) &nbsp; &nbsp; [Retrieve List](268_List_Received_Messages.md) &nbsp; &nbsp; [Delete](270_Delete_an_Incoming_Message.md)|

### Event processing

* [Events Overview](277_Event_Summary.md)
* [Accept External Events](278_Event_Reception.md)
* [Web Socket connection to Event Bus](279_Event_Bus_Connect.md)

#### Event Processing Rule (Cell Control Object)

|Rule|Operations|
|:--|:--|
|Basic Operations|[Create](2A0_Create_Rule.md) &nbsp; &nbsp; [Retrieve](2A1_Retrieve_Rule.md) &nbsp; &nbsp; [List](2A2_Search_Rule.md) &nbsp; &nbsp; [Update](2A3_Update_Rule.md) &nbsp; &nbsp; [Delete](2A4_Delete_Rule.md) |
|&nbsp; &nbsp; Linking with other objects|[Link](2A5_Create_Rule_links.md) &nbsp; &nbsp; [Unlink](2A7_Delete_Rule_links.md) &nbsp; &nbsp; [List Links](2A6_List_Rule_links.md) &nbsp; &nbsp; <br> There is no link update. If you want to update, delete it and recreate it.|
|&nbsp; &nbsp; Bound Object Manipulation|[Create](2A8_Register_Rule_Using_NavProp.md) &nbsp; &nbsp; [List](2A9_List_Using_Rule_NavProp.md)|


#### Event Log 

* [Retrieve Log File](285_Retrieve_Log_File.md)
* [List of Log Files](284_Retrieve_Log_File_list.md)
* [Meatadata of Log File](283_Log_File_Information_Acquisition.md)
* [Delete Log File](286_Delete_Log_File.md)

### Other functions
#### Exporting / Importing the contents inside the Cell

Snapshot file of Cell is created by export execution.  
Import imports the contents of the snapshot file into Cell.  
Snapshot file can be operated with WebDAV interface.  

||Operations|
|:--|:--|
|**Export**|[Execute](501_Export_Cell.md) &nbsp; &nbsp; [Retrieve progress](502_Progress_of_Export_Cell.md)|
|**Import**|[Execute](507_Import_Cell.md) &nbsp; &nbsp; [Retrieve progress](508_Progress_of_Import_Cell.md)|
|**Snapshot**|[Create/Update](503_Register_and_Update_Snapshot_Cell.md) &nbsp; &nbsp; [Retrieve](504_Get_Snapshot_Cell.md) &nbsp; &nbsp; [Retrieve Properties](505_Get_Property_Snapshot_Cell.md) &nbsp; &nbsp; [Delete](506_Delete_Snapshot_Cell.md)|

## Box Level API

The Box Level API is a group of API's that reside on the following Box Root URL and serve for applications and others to manipulate their data. 

#### Box Root URL
```
https://{UnitFQDN}/{CellName}/{BoxName}/
```
Box Level API's are based on an idea of WebDAV file system.  Like ordinary file systems, it is possible to arrange / retrieve files, create / manage folders (collection), get list of files and folders, set / refer to access control, etc.

Also, because it supports the following special collections, it can handle not only file-like data but also various forms of data.  
These special collections can be created in any path on the WebDAV space provided by Box.

|Special collection|Use|Notes|
|:--|:--|:--|
|OData Service Collection|Relational data||
|Engine Service Collection|Run customized logic||
|CALDAV Collection|Calendar data|Unimplemented|
|Link Collection|Aliases to specific areas of other cells or other Box|Unimplemented|



### Basic WebDAV Operations

|Target|Operations|
|:--|:--|
|Collection|[Create](306_Create_Collection.md) &nbsp; &nbsp; [Retrieve Settings](305_Get_Property.md) &nbsp; &nbsp; [Change Settings](308_Change_Property.md) &nbsp; &nbsp; [Move/Rename](309_Update_Move_Collection.md) &nbsp; &nbsp; [Delete](310_Delete_Collection.md)|
|File|[Create/Update](312_Register_and_Update_WebDAV.md) &nbsp; &nbsp; [Retrieve](311_Get_WebDav.md) &nbsp; &nbsp; [Retrieve Settings](307_Get_Property.md) &nbsp; &nbsp; [Change Settings](313_Change_Property.md) &nbsp; &nbsp; [Delete](314_Delete_WebDAV.md)|
|Common|[Configure Access Control](315_Configure_Access_Control.md)|

\* ACL setting (access control setting) is possible for all files and collections (including special collections).  
\* ACL setting can be acquired with the PROPFIND method.

### OData Service Collection

#### Data Manipulation

|User-defined Entity Set|Operations|
|:--|:--|
|Basic Operations|[Create](364_Create_Entity.md) &nbsp; &nbsp; [Retrieve](366_Get_Entity.md) &nbsp; &nbsp; [List](365_List_Entity.md) &nbsp; &nbsp; [Update](367_Update_Entity.md) &nbsp; &nbsp; [Partial Update](369_Partial_Update_Entity.md) &nbsp; &nbsp; [Delete](370_Delete_Entity.md) |
|&nbsp; &nbsp; Linking with other objects|[Link](373_Register_User_Data_links.md) &nbsp; &nbsp; [Unlink](376_Delete_User_Data_links.md) &nbsp; &nbsp; [List Links](374_User_Data_List_links.md) &nbsp; &nbsp; <br> There is no link update. If you want to update, delete it and recreate it.|
|&nbsp; &nbsp; Bound Object Manipulation|[Create](377_Register_using_NavProp.md) &nbsp; &nbsp; [List](378_List_using_NavProp.md)|

* [Batch Operation](368_Entity_Bulk_Operations.md)

#### Schema Definition

||Create|Retrieve|Update|Delete|Other|
|:--|:--|:--|:--|:--|:--|
|**EntityType**|[Create](345_Create_EntityType.md)|[Retrieve](347_Get_EntityType.md)<br>[List](346_List_EntityType.md)|[Update](348_Update_EntityType.md)|[Delete](349_Delete_EntityType.md)||
|_$links|Create|List|Update|Delete||
|_via NavProp||List||||
|**Property**|[Create](355_Register_Property.md)|[Retrieve](357_Get_Property.md)<br>[List](356_List_Property.md)|Update|[Delete](359_Delete_Property.md)||
|_$links|Create|List|Update|Delete||
|**AssociationEnd**|[Create](318_Register_AssociationEnd.md)|[Retrieve](320_Get_AssociationEnd.md)<br>[List](319_List_AssociationEnd.md)|[Update](321_Update_AssociationEnd.md)|[Delete](322_Delete_AssociationEnd.md)||
|_$links|[Create](323_Register_AssociationEnd_links.md)|[List](324_List_AssociationEnd_links.md)||[Delete](325_Delete_AssociationEnd_links.md)||
|_via NavProp||List||||
|**ComplexType**|[Create](327_Register_ComplexType.md)|[Retrieve](329_Get_ComplexType.md)<br>[List](328_List_ComplexType.md)|Update|[Delete](331_Delete_ComplexType.md)||
|_$links|Create|List|Update|Delete||
|**ComplexTypeProperty**|[Create](336_Register_ComplexTypeProperty.md)|[Retrieve](338_Get_ComplexTypeProperty.md)<br>[List](337_List_ComplexTypeProperty.md)|[Update](339_Update_ComplexTypeProperty.md)|[Delete](340_Delete_ComplexTypeProperty.md)||
|_$links|Create|List|Update|Delete||

##### Service Document Retrieve/Schema Retrieve

||Retrieve|
|:--|:--|
|Service Document|[Retrieve](317_Document_Acquisition_Service.md)|
|Schema|[Retrieve](316_User_Defined_Data_Schema.md)|


### Engine Service Collection
You can register Personium application and server side logic created by Cell user and run it.  
First, register the user logic as a file, set the service collection and associate with the path, so that  
You can run the user logic for requests from any path under the collection.

||Create|Retrieve|Update|Delete|Other|
|:--|:--|:--|:--|:--|:--|
|Service Collection Source|[Create](381_Create_Service_Collection_Source.md)|[Retrieve](382_List_Service_Collection_Source.md)|[Apply Settings](380_Configure_Service_Collection.md)|[Delete](383_Delete_Service_Collection_Source.md)|[Service Execute](384_Service_Execution.md)|

## Common Information

### OData Acquisition Common Queries

|Query|Single Acquisition|List Acquisition|
|:--|:--|:--|
|[$format Query](404_Format_Query.md)|Yes|Yes|
|[$expand Query](405_Expand_Query.md)|Yes|Yes|
|[$select Query](406_Select_Query.md)|Yes|Yes|
|[$orderby Query](400_Orderby_Query.md)|No|Yes|
|[$top Query](401_Top_Query.md)|No|Yes|
|[$skip Query](402_Skip_Query.md)|No|Yes|
|[$filter Query](403_Filter_Query.md)|No|Yes|
|[$inlinecount](407_Inlinecount_Query.md)|No|Yes|
|[Full-text Search (q) Query](408_Full_Text_Search_Query.md)|No|Yes|

#### [Error Messages](004_Error_Messages.md)

#### [Restrictions on Personium HTTP Implementation](003_Common_Limitations_on_HTTP_Implementation.md)

#### [CORS Support](002_CORS_Support.md)

#### [Cross Domain Policy File Retrieve](001_Cross_Domain_Policy_File.md)

