\# BauRaster API V1



\## Authentifizierung



\### Login



POST /api/auth/login



\### Logout



POST /api/auth/logout



\### Refresh Token



POST /api/auth/refresh



\---



\## Projekte



GET /api/projects



GET /api/projects/{id}



POST /api/projects



PUT /api/projects/{id}



DELETE /api/projects/{id}



POST /api/projects/{id}/archive



\---



\## Kunden



GET /api/customers



GET /api/customers/{id}



POST /api/customers



PUT /api/customers/{id}



DELETE /api/customers/{id}



\---



\## Termine



GET /api/appointments



POST /api/appointments



PUT /api/appointments/{id}



DELETE /api/appointments/{id}



\---



\## Aufgaben



GET /api/tasks



POST /api/tasks



PUT /api/tasks/{id}



DELETE /api/tasks/{id}



\---



\## Fotos



POST /api/photos/upload



GET /api/projects/{id}/photos



DELETE /api/photos/{id}



\---



\## Dokumente



POST /api/documents/upload



GET /api/projects/{id}/documents



DELETE /api/documents/{id}



