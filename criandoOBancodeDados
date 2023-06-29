# bdecommerce
Construindo seu Primeiro Projeto Lógico de Banco de Dados

-- criação de banco de dados para o cenario e-commerce
create database ecommerce;
use ecommerce;

-- criar tabelas cliente
create table clients(
	idClient int auto_increment primary key,
    Fname varchar(10),
    Minit varchar(3),
    Lname varchar(20),
    CPF char(11) not null,
    address varchar(30),
    constraint unique_cpf_client unique (CPF)    
);
alter table clients auto_increment=1;
-- criar tabelas produto
create table product(
	idProduct int auto_increment primary key,
    Pname varchar(10) not null,
    Classification_kids bool default false,
    category enum("Eletronico","vestimenta","brinquedos","alimento","moveis") not null,    
    Avaliation float default 0,
    size varchar(10)      
);
alter table product auto_increment=1;
-- criar tabelas pedido 
create table orders (
	idOrders int auto_increment primary key,
    idOrdersClient int,
    ordersState enum("Cancelado", "Confirmado", "Em processamento"),
    ordersDescription varchar(255),
    sendValue float default 10,
    payment enum("Credit Card","Debit Card", "Cash") not null,
    constraint fk_orders_client foreign key (idOrdersClient) references clients(idClient)
);
alter table orders auto_increment=1;
--  criar tabela estoque
create table productStorage(
	idProdStorage int auto_increment primary key,
    storageLocation varchar(255) not null,
    storageQuantity int default 0    
);
alter table productStorage auto_increment=1;
-- Tabela fornecedor e vendedor unidas na tabela employee
 
-- criar tabela employee
alter table employee modify column CNPJ char(15);
create table employee(
	idEmployee int auto_increment primary key,
    socialName varchar(255),
    CPF char(11) not null, 
    CNPJ char(15),
    address varchar(255) not null,
    fantasyName varchar(255),
    contact varchar(24) default 0,
    activity enum("supplier","saller") not null,
    constraint unique_socialName unique (socialName),
	constraint unique_CPF unique (CPF),
	constraint unique_CNPJ unique (CNPJ)
);
alter table employee auto_increment=1;

-- criar tabela produto-empregado
create table employeeToProduct(
	idEmployee int,
    idProduct int,
    prodQuantity int default 1,
    primary key (idEmployee, idProduct),
    constraint fk_employee foreign key (idEmployee) references employee(idEmployee),
	constraint fk_product foreign key (idproduct) references product(idProduct)
);
-- criar tabela produto-estoque
create table storageToProduct(
	idProdStorage int,
    idProduct int,
    primary key (idProdStorage, idProduct),
    constraint fk_productStorage foreign key (idProdStorage) references productStorage(idProdStorage),
	constraint fk_product_id foreign key (idproduct) references product(idProduct)
);
-- criar tabela produto-pedido
ALTER TABLE ordersToProduct ADD CONSTRAINT fk_id_product foreign key (idProduct) references product(idProduct); 
create table ordersToProduct(
	idOrders int,
    idProduct int,
    quantity int not null,
    status ENUM("Disponivel", "Sem estoque") default "Disponivel",
    primary key (idOrders, idProduct),
    constraint fk_idOrders foreign key (idOrders) references orders(idOrders),
	constraint fk_id_product foreign key (idProduct) references product(idProduct)
);
