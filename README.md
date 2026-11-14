# SQL_BANCO_DE_DADOS_BIBLIOTECA
create database biblioteca;
use biblioteca;

CREATE TABLE IF NOT EXISTS `livro` (
	`id_livro` int AUTO_INCREMENT NOT NULL UNIQUE,
	`titulo` int NOT NULL,
	`isbn` int NOT NULL,
	`id_editora` int NOT NULL,
	`id_categoria` int NOT NULL,
	PRIMARY KEY (`id_livro`)
);
CREATE TABLE IF NOT EXISTS `livro_autor` (
	`id_livro` int AUTO_INCREMENT NOT NULL UNIQUE,
	`id_autor` int NOT NULL,
	`id_livro_autor` int NOT NULL,
	`uq_livro,autor` int NOT NULL,
	PRIMARY KEY (`id_livro_autor`)
);
CREATE TABLE IF NOT EXISTS `autor` (
	`id_autor` int AUTO_INCREMENT NOT NULL UNIQUE,
	`nome` int NOT NULL,
	PRIMARY KEY (`id_autor`)
);
CREATE TABLE IF NOT EXISTS `livro_palavra` (
	`id_livro` int AUTO_INCREMENT NOT NULL UNIQUE,
	`id_palavra` int NOT NULL,
	`id_livro_palavra` int NOT NULL,
	`uq_livro_palavra` int NOT NULL,
	PRIMARY KEY (`id_livro`)
);
CREATE TABLE IF NOT EXISTS `palavra_chave` (
	`id_palavra` int AUTO_INCREMENT NOT NULL UNIQUE,
	`descricao` int NOT NULL,
	PRIMARY KEY (`id_palavra`)
);
CREATE TABLE IF NOT EXISTS `editora` (
	`id_editora` int AUTO_INCREMENT NOT NULL UNIQUE,
	`nome` int NOT NULL,
	`cidade` int NOT NULL,
	PRIMARY KEY (`id_editora`)
);
CREATE TABLE IF NOT EXISTS `categoria` (
	`id_categoria` int AUTO_INCREMENT NOT NULL UNIQUE,
	`descricao` int NOT NULL,
	PRIMARY KEY (`id_categoria`)
);
ALTER TABLE `livro` ADD CONSTRAINT `livro_fk3` FOREIGN KEY (`id_editora`) REFERENCES `editora`(`id_editora`);
ALTER TABLE `livro` ADD CONSTRAINT `livro_fk4` FOREIGN KEY (`id_categoria`) REFERENCES `categoria`(`id_categoria`);
ALTER TABLE `livro_autor` ADD CONSTRAINT `livro_autor_fk0` FOREIGN KEY (`id_livro`) REFERENCES `livro`(`id_livro`);
ALTER TABLE `livro_autor` ADD CONSTRAINT `livro_autor_fk1` FOREIGN KEY (`id_autor`) REFERENCES `autor`(`id_autor`);
ALTER TABLE `livro_palavra` ADD CONSTRAINT `livro_palavra_fk0` FOREIGN KEY (`id_livro`) REFERENCES `livro`(`id_livro`);
ALTER TABLE `livro_palavra` ADD CONSTRAINT `livro_palavra_fk1` FOREIGN KEY (`id_palavra`) REFERENCES `palavra_chave`(`id_palavra`);
