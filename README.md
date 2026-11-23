# Sistema-de-Vendas

Nome do projeto: Sistema-de-vendas

Integrantes da equipe: Kaique Santiago De Freitas

Descrição do sistema: Sistema que gerencia produtos, vendas e clientes de uma empresa de cosméticos

Tecnologias utilizadas: Java, JavaFX, MySQL, Jaspersoft, Drawio(diagramas)

Como configurar o banco de dados: Ative o MySQL Server (localhost:3306, usuário root e senha root, conforme Conexao.java) e execute o script SQL para criar o banco sistema_vendas e as tabelas cliente, produto e venda.


CREATE DATABASE IF NOT EXISTS sistema_vendas;
USE sistema_vendas;

CREATE TABLE IF NOT EXISTS cliente (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    status VARCHAR(30) NOT NULL DEFAULT 'Ativo',
    data_cadastro DATE NOT NULL
);

CREATE TABLE IF NOT EXISTS produto (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    categoria VARCHAR(60) NOT NULL,
    preco_compra DECIMAL(10, 2) NOT NULL,
    preco_venda DECIMAL(10, 2) NOT NULL,
    quantidade INT NOT NULL
);

CREATE TABLE IF NOT EXISTS venda (
    id INT AUTO_INCREMENT PRIMARY KEY,
    cliente_id INT NOT NULL,
    produto_id INT NOT NULL,
    quantidade INT NOT NULL,
    valor_total DECIMAL(10, 2) NOT NULL,
    lucro DECIMAL(10, 2) NOT NULL,
    data_venda DATE NOT NULL,
    pago BOOLEAN NOT NULL DEFAULT FALSE,
    FOREIGN KEY (cliente_id) REFERENCES cliente(id),
    FOREIGN KEY (produto_id) REFERENCES produto(id)
);

Como executar o sistema:
Importe o projeto SistemaVendasFx no Eclipse, adicione o JavaFX SDK, o mysql-connector-j e os .jar da pasta lib/ (JasperReports) ao Build Path, configure os VM Arguments do JavaFX (--module-path e --add-modules javafx.controls,javafx.fxml) e execute AppSistemaVendas.java.

Funcionalidades implementadas:
Produtos: CRUD completo com ID automático ou manual, categorias (Capilar, Corporal, Estético, Eletrodoméstico, Perfumaria) e controle de estoque.

Clientes: CRUD completo com ID automático ou manual, status e cálculo automático de saldo A Pagar (R
) e LucroObtido(R).

Vendas: Registro de vendas com cálculo automático de valor total e lucro, baixa no estoque e controle de status (Pago / Não Pago).

Relatórios (JasperReports): Emissão dos relatórios de Vendas e Lucros e Cobrança (Em Aberto).
Informações sobre a versão entregue: 1.0

