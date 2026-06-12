\# BauRaster Datenbank V1



\## Projects



\- ProjectId

\- ProjectNumber

\- Name

\- CustomerId

\- AddressId

\- PhaseId

\- StatusId



\## Customers



\- CustomerId

\- CompanyName

\- ContactPerson

\- Phone

\- Email

\# BauRaster Datenbank V1



\## Grundprinzip



Das zentrale Objekt der Anwendung ist das Bauvorhaben (Projekt).



Alle weiteren Daten werden einem Projekt zugeordnet.



\## Haupttabellen



\### Projects



\* ProjectId

\* ProjectNumber

\* Name

\* Description

\* CustomerId

\* AddressId

\* PhaseId

\* StatusId

\* Priority

\* Progress

\* CreatedAt

\* UpdatedAt



\### Customers



\* CustomerId

\* CompanyName

\* ContactPerson

\* Phone

\* Email

\* Notes



\### Addresses



\* AddressId

\* Street

\* HouseNumber

\* ZipCode

\* City

\* Country

\* Latitude

\* Longitude



\### Users



\* UserId

\* FirstName

\* LastName

\* Email

\* RoleId



\### Roles



\* RoleId

\* Name



\### Tasks



\* TaskId

\* ProjectId

\* AssignedUserId

\* Title

\* DueDate

\* Status



\### Appointments



\* AppointmentId

\* ProjectId

\* AssignedUserId

\* StartDate

\* EndDate



\### Photos



\* PhotoId

\* ProjectId

\* Category

\* FileName

\* StoragePath



\### Documents



\* DocumentId

\* ProjectId

\* DocumentType

\* FileName

\* StoragePath

\## Tabelle: Projects



| Feld          | Typ          | Pflicht |

| ------------- | ------------ | ------- |

| ProjectId     | UUID         | Ja      |

| ProjectNumber | VARCHAR(50)  | Ja      |

| Name          | VARCHAR(255) | Ja      |

| Description   | TEXT         | Nein    |

| CustomerId    | UUID         | Ja      |

| AddressId     | UUID         | Ja      |

| PhaseId       | INTEGER      | Ja      |

| StatusId      | INTEGER      | Ja      |

| Priority      | INTEGER      | Ja      |

| Progress      | INTEGER      | Ja      |

| IsArchived    | BOOLEAN      | Ja      |

| CreatedAt     | TIMESTAMP    | Ja      |

| UpdatedAt     | TIMESTAMP    | Ja      |



\### Beziehungen



\* Customer 1:n Projects

\* Address 1:n Projects

\* Project 1:n Tasks

\* Project 1:n Appointments

\* Project 1:n Photos

\* Project 1:n Documents

\* Project 1:n ProjectHistory



\### Indizes



\* ProjectNumber

\* CustomerId

\* PhaseId

\* StatusId

\* CreatedAt

\## Tabelle: Customers



| Feld          | Typ          | Pflicht |

| ------------- | ------------ | ------- |

| CustomerId    | UUID         | Ja      |

| CompanyName   | VARCHAR(255) | Ja      |

| ContactPerson | VARCHAR(255) | Nein    |

| Phone         | VARCHAR(100) | Nein    |

| Email         | VARCHAR(255) | Nein    |

| Website       | VARCHAR(255) | Nein    |

| Notes         | TEXT         | Nein    |

| CreatedAt     | TIMESTAMP    | Ja      |

| UpdatedAt     | TIMESTAMP    | Ja      |



\### Beziehungen



\* Customer 1:n Projects



\### Indizes



\* CompanyName

\* ContactPerson

\* Email



\---



\## Tabelle: Addresses



| Feld        | Typ           | Pflicht |

| ----------- | ------------- | ------- |

| AddressId   | UUID          | Ja      |

| Street      | VARCHAR(255)  | Ja      |

| HouseNumber | VARCHAR(50)   | Nein    |

| ZipCode     | VARCHAR(20)   | Ja      |

| City        | VARCHAR(100)  | Ja      |

| Country     | VARCHAR(100)  | Ja      |

| Latitude    | DECIMAL(10,7) | Nein    |

| Longitude   | DECIMAL(10,7) | Nein    |

| CreatedAt   | TIMESTAMP     | Ja      |

| UpdatedAt   | TIMESTAMP     | Ja      |



\### Beziehungen



\* Address 1:n Projects



\### Indizes



\* ZipCode

\* City

\* Latitude, Longitude



\---



\## Tabelle: Roles



| Feld         | Typ          | Pflicht |

| ------------ | ------------ | ------- |

| RoleId       | UUID         | Ja      |

| Name         | VARCHAR(100) | Ja      |

| Description  | TEXT         | Nein    |

| IsSystemRole | BOOLEAN      | Ja      |

| CreatedAt    | TIMESTAMP    | Ja      |



\### Standardrollen



\* Administrator

\* Büro

\* Bauleiter

\* Mitarbeiter

\* Gast



\### Beziehungen



\* Role 1:n Users



\### Indizes



\* Name



\---



\## Tabelle: Users



| Feld         | Typ          | Pflicht |

| ------------ | ------------ | ------- |

| UserId       | UUID         | Ja      |

| FirstName    | VARCHAR(100) | Ja      |

| LastName     | VARCHAR(100) | Ja      |

| Email        | VARCHAR(255) | Ja      |

| Phone        | VARCHAR(100) | Nein    |

| PasswordHash | TEXT         | Ja      |

| RoleId       | UUID         | Ja      |

| IsActive     | BOOLEAN      | Ja      |

| LastLoginAt  | TIMESTAMP    | Nein    |

| CreatedAt    | TIMESTAMP    | Ja      |

| UpdatedAt    | TIMESTAMP    | Ja      |



\### Beziehungen



\* Role 1:n Users

\* User 1:n Tasks

\* User 1:n Appointments

\* User 1:n Photos

\* User 1:n Documents

\* User 1:n ProjectHistory



\### Indizes



\* Email

\* RoleId

\* IsActive

\## Tabelle: Tasks



| Feld           | Typ          | Pflicht |

| -------------- | ------------ | ------- |

| TaskId         | UUID         | Ja      |

| ProjectId      | UUID         | Ja      |

| AssignedUserId | UUID         | Ja      |

| Title          | VARCHAR(255) | Ja      |

| Description    | TEXT         | Nein    |

| Priority       | INTEGER      | Ja      |

| Status         | VARCHAR(50)  | Ja      |

| DueDate        | TIMESTAMP    | Nein    |

| CompletedAt    | TIMESTAMP    | Nein    |

| CreatedAt      | TIMESTAMP    | Ja      |

| UpdatedAt      | TIMESTAMP    | Ja      |



\### Beziehungen



\* Project 1:n Tasks

\* User 1:n Tasks



\### Indizes



\* ProjectId

\* AssignedUserId

\* Status

\* DueDate



\---



\## Tabelle: Appointments



| Feld           | Typ          | Pflicht |

| -------------- | ------------ | ------- |

| AppointmentId  | UUID         | Ja      |

| ProjectId      | UUID         | Ja      |

| AssignedUserId | UUID         | Ja      |

| Title          | VARCHAR(255) | Ja      |

| Description    | TEXT         | Nein    |

| StartDate      | TIMESTAMP    | Ja      |

| EndDate        | TIMESTAMP    | Ja      |

| Status         | VARCHAR(50)  | Ja      |

| CreatedAt      | TIMESTAMP    | Ja      |

| UpdatedAt      | TIMESTAMP    | Ja      |



\### Beziehungen



\* Project 1:n Appointments

\* User 1:n Appointments



\### Indizes



\* ProjectId

\* AssignedUserId

\* StartDate



\---



\## Tabelle: Photos



| Feld        | Typ           | Pflicht |

| ----------- | ------------- | ------- |

| PhotoId     | UUID          | Ja      |

| ProjectId   | UUID          | Ja      |

| Category    | VARCHAR(50)   | Ja      |

| FileName    | VARCHAR(255)  | Ja      |

| StoragePath | TEXT          | Ja      |

| Latitude    | DECIMAL(10,7) | Nein    |

| Longitude   | DECIMAL(10,7) | Nein    |

| CreatedBy   | UUID          | Ja      |

| CreatedAt   | TIMESTAMP     | Ja      |



\### Kategorien



\* Vorher

\* Während

\* Nachher

\* Mangel

\* Abnahme



\### Beziehungen



\* Project 1:n Photos

\* User 1:n Photos



\### Indizes



\* ProjectId

\* Category

\* CreatedAt



\---



\## Tabelle: Documents



| Feld         | Typ          | Pflicht |

| ------------ | ------------ | ------- |

| DocumentId   | UUID         | Ja      |

| ProjectId    | UUID         | Ja      |

| DocumentType | VARCHAR(100) | Ja      |

| FileName     | VARCHAR(255) | Ja      |

| StoragePath  | TEXT         | Ja      |

| UploadedBy   | UUID         | Ja      |

| UploadedAt   | TIMESTAMP    | Ja      |



\### Dokumenttypen



\* Angebot

\* Auftrag

\* Rechnung

\* Plan

\* Vertrag

\* PDF

\* Sonstiges



\### Beziehungen



\* Project 1:n Documents

\* User 1:n Documents



\### Indizes



\* ProjectId

\* DocumentType

\* UploadedAt

\## Tabelle: Notes



| Feld      | Typ       | Pflicht |

| --------- | --------- | ------- |

| NoteId    | UUID      | Ja      |

| ProjectId | UUID      | Ja      |

| CreatedBy | UUID      | Ja      |

| NoteText  | TEXT      | Ja      |

| CreatedAt | TIMESTAMP | Ja      |



\### Beziehungen



\* Project 1:n Notes

\* User 1:n Notes



\### Indizes



\* ProjectId

\* CreatedAt



\---



\## Tabelle: ProjectHistory



| Feld      | Typ          | Pflicht |

| --------- | ------------ | ------- |

| HistoryId | UUID         | Ja      |

| ProjectId | UUID         | Ja      |

| UserId    | UUID         | Ja      |

| Action    | VARCHAR(255) | Ja      |

| OldValue  | TEXT         | Nein    |

| NewValue  | TEXT         | Nein    |

| CreatedAt | TIMESTAMP    | Ja      |



\### Beispiele



\* Projekt erstellt

\* Status geändert

\* Termin erstellt

\* Foto hochgeladen

\* Dokument hinzugefügt

\* Projekt archiviert



\### Beziehungen



\* Project 1:n ProjectHistory

\* User 1:n ProjectHistory



\### Indizes



\* ProjectId

\* CreatedAt



\---



\## Tabelle: ProjectPhases



| PhaseId | Name         |

| ------- | ------------ |

| 1       | Aufnahme     |

| 2       | Termin       |

| 3       | KV in Arbeit |

| 4       | KV versendet |

| 5       | Auftrag      |

| 6       | Ausführung   |

| 7       | Fotodok      |

| 8       | Abschluss    |

| 9       | Archiv       |



\---



\## Tabelle: ProjectStatuses



| Feld      | Typ          |

| --------- | ------------ |

| StatusId  | INTEGER      |

| PhaseId   | INTEGER      |

| Name      | VARCHAR(100) |

| Color     | VARCHAR(20)  |

| SortOrder | INTEGER      |



\### Beispiele



\* Neu

\* Geplant

\* Offen

\* Prüfen

\* Läuft

\* Blockiert

\* Erledigt



\### Beziehungen



\* ProjectPhase 1:n ProjectStatuses



\### Indizes



\* PhaseId

\* Name



