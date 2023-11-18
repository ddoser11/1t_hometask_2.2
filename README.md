CREATE TABLE if not exists Readers(
	reader_id serial PRIMARY KEY,
	first_name VARCHAR (40) NOT NULL,
	last_name VARCHAR (40) NOT NULL,
	middle_name VARCHAR (40) NOT NULL,
	adress VARCHAR ( 255 ) NOT NULL,
	phone char(20) NOT NULL 
);

CREATE TABLE if not exists authors(
	author_id serial PRIMARY KEY,
	first_name VARCHAR (40) NOT NULL,
	last_name VARCHAR (40) NOT NULL,
	middle_name VARCHAR (40) NOT NULL
);

CREATE TABLE if not exists publishing_houses(
	id_publishing serial PRIMARY KEY,
	publishing_name VARCHAR (100) NOT NULL,
	city VARCHAR (40) NOT NULL
);

CREATE TABLE if not exists books(
	book_id serial PRIMARY KEY,
	price BIGINT,
	pages BIGINT,
	amount BIGINT,
	publish_year date NOT NULL,
	id_publishing bigint,
	FOREIGN KEY(id_publishing) REFERENCES publishing_houses(id_publishing) ON DELETE CASCADE
);

CREATE TABLE if not exists books_with_readers(
	id serial PRIMARY KEY,
	reader_id int, 
	book_id BIGINT, 
	book_date_taken date NOT NULL,
	deadline date NOT NULL,
	FOREIGN KEY(reader_id) REFERENCES Readers(reader_id) ON DELETE CASCADE,
	FOREIGN KEY(book_id) REFERENCES books(book_id) ON DELETE CASCADE
);
CREATE TABLE if not exists books_and_author(
	id serial PRIMARY KEY,
	book_id BIGINT,
	author_id BIGINT,
	FOREIGN KEY(book_id) REFERENCES books(book_id) ON DELETE CASCADE,
	FOREIGN KEY(author_id) REFERENCES authors(author_id) ON DELETE CASCADE
	);
