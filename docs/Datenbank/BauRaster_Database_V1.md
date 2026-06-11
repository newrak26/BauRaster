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



