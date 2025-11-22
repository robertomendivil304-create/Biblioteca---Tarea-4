Implementación de una base de datos NoSQL en MongoDB

El caso de uso seleccionado es: catálogo de libros y autores.

Para este trabajo se selecciona como caso de uso la creación de un catálogo digital de libros, el cual contiene información de autores y sus obras. Este tipo de aplicación es ideal para una base de datos NoSQL como MongoDB debido a su flexibilidad, escalabilidad y manejo de datos semi-estructurados.

Diseño del esquema de la base de datos.

1.	Colecciones

Se diseñan dos colecciones principales:

a.	Colección: authors, que abarca los siguientes campos:

•	Name: nombre del autor.

•	Birth year: año de nacimiento.

•	Nationality: nacionalidad.

b.	Colección: books, que abarca los siguientes campos:

•	Título: título del libro.

•	Autor: nombre del autor.

•	Género: categoría literaria.

•	Anio: año de publicación.

4.	Implementación en mongoDB.
   
•	Se creó una base de datos llamada use biblioteca.

•	Se insertaron 4 autores reales en authors y 100 libros distribuidos entre esos autores en books.

6.	Consultas básicas.
   
a.	Insertar un libro:db.books.insertOne({titulo: "Nuevo Libro",autor: "Isabel Allende",genero: "Drama",anio: 2024})

b.	Seleccionar documentos:

Todos los libros:

Db.books.find( )

c.	Actualizar documentos:

Modificar el género de un libro:

db.books.updateOne(
  { titulo: "El otoño del cuento" },
  { $set: { genero: "Realismo mágico clásico" } })
  
d.	Eliminar documentos:

db.books.deleteOne ({título: “el otoño del cuento”})

Consultas con filtros y operadores:

a.	Libros de un género específico:
db.books.find ({"genero": { $regex: "^drama$", $options: "i" }})

b.	Libros de un autor específico
db.books.find ({"autor": { $regex: "^Gabriel García Márquez$", $options: "i" }
})

c.	Libros entre dos años:

db.books.find({ "anio": { $gte: 2000, $lte: 2014 }})

8.	Consultas de agregacion:
   
a.	Contar libros por autor;
db.books.aggregate({ "autor": { $regex: "^Gabriel García Márquez$", $options: "i" } })
b.	Cantidad total de libros:
db.books.countDocuments()


