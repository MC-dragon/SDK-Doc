---
title: Document properties
SortOrder: 10
uid: crmscript_doc_properties
---

## Retrieve document info

### To view basic info, use NSDocument

```crmscript!
NSDocumentAgent docAgent;
NSDocument doc = docAgent.GetDocument(2);
printLine(doc.GetDocumentName());
```

### To view (and possibly update) complex info, use NSDocumentEntity

```crmscript!
NSDocumentAgent docAgent;
NSDocumentEntity doc = docAgent.GetDocumentEntity(1);
printLine(doc.GetContact().GetName());
```

### List all documents with SearchEngine

```crmscript!
SearchEngine se;
se.addFields("document", "document_id,name,header");
print(se.executeTextTable());
```

> [!TIP]
> If you know there's a lot of documents, consider adding a **count** criteria to limit the results.

### NSDocument[] GetDocumentList(Integer[] p0)

Fetches a collection of appointments corresponding to a list of IDs.

```crmscript!
Integer[] docIDs;
docIDs.pushFront(84);
docIDs.pushFront(86);
docIDs.pushFront(88);

NSDocumentAgent docAgent;
NSDocument[] docList = docAgent.GetDocumentList(docIDs);

for(Integer i = 0; i < docList.length(); i++) {
  printLine(docList[i].GetDocumentId().toString());
}
```

### NSDocument[] GetAppointmentDocuments(Integer appointmentId)

Get all documents that are linked to an appointment.

```crmscript
Integer appointmentId = 4;
NSDocumentAgent docAgent;
NSDocument[] docList = docAgent.GetAppointmentDocuments(appointmentId);
```

### NSDocument[] GetContactDocuments(Integer contactId, DateTime startTime, DateTime endTime, Integer count)

Fetches a limited number of documents within a time range for the given contact.

```crmscript
NSDocumentAgent docAgent;
DateTime start;
DateTime end;

NSDocument[] docList = docAgent.GetContactDocuments(4, start.addMonth(-6), end, 10);
```

> [!TIP]
> Set `count` to -1 to not restrict the collection of documents retrieved.

## Create document entity

### NSDocumentEntity CreateDefaultDocumentEntity()

Create and populate with default values:

```crmscript!
NSDocumentAgent agent;
NSDocumentEntity doc = agent.CreateDefaultDocumentEntity();

doc.SetHeader("Test document");
doc.SetName("Test.doc");

doc = agent.SaveDocumentEntity(doc);

printLine(doc.GetDocumentId().toString());
```

## Change document properties

> [!NOTE]
> The `NSDocumentEntity` can't be changed if the document is marked as **Completed**.<br />Use `GetCompleted()` to check the status. Toggle it to **0** to do your edits and then toggle it back if applicable.

```crmscript
NSDocumentAgent docAgent;

NSDocumentEntity doc = docAgent.GetDocumentEntity(2);

if (doc.GetCompleted() == 3) {
  doc.SetCompleted(0);
  doc = docAgent.SaveDocumentEntity(doc);
}
```

## Delete document entity

```crmscript
NSDocumentAgent agent;
agent.DeleteDocumentEntity(99);
```

## Reference

### Frequently used fields

| Field          | Description                             |
|:---------------|:----------------------------------------|
| document_id    | ID                                      |
| application_id | application this document was made with |
| name           | filename with extension                 |
| header         | visible document name aka title         |
| our_ref        | our reference (internal)                |
| your_ref       | your reference (external)               |
| appointment_id | points back to owning appointment       |

For a complete list of fields, see the [database reference](https://community.superoffice.com/documentation/SDK/SO.Database/html/Tables-document.htm).

> [!TIP]
> Both `our_ref` and `your_ref` are strings.

### Timestamp values

| Field         | Description                                              |
|:--------------|:---------------------------------------------------------|
| registered    | UtcDateTime of registration                              |
| updated       | UtcDateTime of last update                               |