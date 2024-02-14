# API de un sistema de reserva de butacas de cine

En este ejercicio vamos a diseñar la API REST para el cine en el que venimos trabajando en los ejercicios de los anteriores temas.

Las operaciones que la API debe soportar son las siguientes:
- Crear, eliminar y modificar películas.
- Crear, eliminar y modificar (parcialmente) salas.
- Crear, eliminar y modificar (parcialmente) usuarios.
- Crear una reserva para un usuario en una sala.
- Cancelar una reserva para un usuario en una sala.
- Modificar una reserva para un usuario en una sala.
- Registrar un pago de una reserva.

| Método HTTP                            | URI                   | Query Params  | Cuerpo de la Petición                                 | Cuerpo de la Respuesta                | Códigos de Respuesta                                |
|----------------------------------------|-----------------------|---------------|-----------------------------------------|---------------------------------------|---------------------------------------------------|
| POST                                   | /movies                 | N/A          | `{"title": "Wakanda Forever", "image": "./wakanda.png", "synopsis": "A sequel that will continue to explore the incomparable world of Wakanda and all the rich and varied characters introduced in the 2018 film.", "time": "2h 41m", "category": "Science fiction", "score": "4"}`                           | `{"movieId": 1, "title": "Wakanda Forever", "image": "./wakanda.png", "synopsis": "A sequel that will continue to explore the incomparable world of Wakanda and all the rich and varied characters introduced in the 2018 film.", "time": "2h 41m", "category": "Science fiction", "score": "4"}`             | 201 Created<br/>400 Bad Request<br/>500 Internal Server Error |
| POST                                   | /rooms                 | N/A          | `{"Name": "A1", "quantityCols": 4, "quantityRows": 4}`                     | `{"roomId": 100, "Name": "A1", "quantityCols": 4, "quantityRows": 4}`             | 201 Created<br/>400 Bad Request<br/>500 Internal Server Error |
| POST                                   | /users                 | N/A          | `{"idDocument": "1037661", "Name": "Catalina", "LastName": "Valencia Gaviria", "Email": "cvalenciagav@gmail.com", "Phone": "31994540045"}`                     | `{"userId": 14566, "idDocument": "1037661", "Name": "Catalina", "LastName": "Valencia Gaviria", "Email": "cvalenciagav@gmail.com", "Phone": "31994540045"}`             | 201 Created<br/>400 Bad Request<br/>500 Internal Server Error |
| POST                                   | /reservations                 | N/A          | `{"userId": 14566, "roomId": 100, "Date": "2024-01-5", "cost": "$12.000", "status": "pending payment"}`               | `{"reservationId": 1000, "userId": 14566, "roomId": 100, "Date": "2024-01-5"}, "cost": "$12.000", "status": "pending payment"`             | 201 Created<br/>400 Bad Request<br/>500 Internal Server Error |
| POST                                   | /payments                 | N/A          | `{"reservationId": 1000, "value": 12000, "DateCreated": "2024-01-12"}`     | `{"paymentId": 45656, "reservationId": 1000, "value": 12000, "DateCreated": "2024-01-12"}`             | 201 Created<br/>400 Bad Request<br/>500 Internal Server Error |