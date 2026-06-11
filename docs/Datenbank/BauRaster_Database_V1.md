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



