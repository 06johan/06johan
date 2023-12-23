USE [master] 

GO 

/****** Object:  Database [TechSolutionsDB]    Script Date: 12/19/2023 8:23:28 PM ******/ 

CREATE DATABASE [TechSolutionsDB] 

 CONTAINMENT = NONE 

 ON  PRIMARY  

( NAME = N'TechSolutionsDB', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\TechSolutionsDB.mdf' , SIZE = 8192KB , MAXSIZE = UNLIMITED, FILEGROWTH = 65536KB ) 

 LOG ON  

( NAME = N'TechSolutionsDB_log', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\TechSolutionsDB_log.ldf' , SIZE = 8192KB , MAXSIZE = 2048GB , FILEGROWTH = 65536KB ) 

 WITH CATALOG_COLLATION = DATABASE_DEFAULT, LEDGER = OFF 

GO 

ALTER DATABASE [TechSolutionsDB] SET COMPATIBILITY_LEVEL = 160 

GO 

IF (1 = FULLTEXTSERVICEPROPERTY('IsFullTextInstalled')) 

begin 

EXEC [TechSolutionsDB].[dbo].[sp_fulltext_database] @action = 'enable' 

end 

GO 

ALTER DATABASE [TechSolutionsDB] SET ANSI_NULL_DEFAULT OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET ANSI_NULLS OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET ANSI_PADDING OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET ANSI_WARNINGS OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET ARITHABORT OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET AUTO_CLOSE ON  

GO 

ALTER DATABASE [TechSolutionsDB] SET AUTO_SHRINK OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET AUTO_UPDATE_STATISTICS ON  

GO 

ALTER DATABASE [TechSolutionsDB] SET CURSOR_CLOSE_ON_COMMIT OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET CURSOR_DEFAULT  GLOBAL  

GO 

ALTER DATABASE [TechSolutionsDB] SET CONCAT_NULL_YIELDS_NULL OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET NUMERIC_ROUNDABORT OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET QUOTED_IDENTIFIER OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET RECURSIVE_TRIGGERS OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET  ENABLE_BROKER  

GO 

ALTER DATABASE [TechSolutionsDB] SET AUTO_UPDATE_STATISTICS_ASYNC OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET DATE_CORRELATION_OPTIMIZATION OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET TRUSTWORTHY OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET ALLOW_SNAPSHOT_ISOLATION OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET PARAMETERIZATION SIMPLE  

GO 

ALTER DATABASE [TechSolutionsDB] SET READ_COMMITTED_SNAPSHOT OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET HONOR_BROKER_PRIORITY OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET RECOVERY SIMPLE  

GO 

ALTER DATABASE [TechSolutionsDB] SET  MULTI_USER  

GO 

ALTER DATABASE [TechSolutionsDB] SET PAGE_VERIFY CHECKSUM   

GO 

ALTER DATABASE [TechSolutionsDB] SET DB_CHAINING OFF  

GO 

ALTER DATABASE [TechSolutionsDB] SET FILESTREAM( NON_TRANSACTED_ACCESS = OFF )  

GO 

ALTER DATABASE [TechSolutionsDB] SET TARGET_RECOVERY_TIME = 60 SECONDS  

GO 

ALTER DATABASE [TechSolutionsDB] SET DELAYED_DURABILITY = DISABLED  

GO 

ALTER DATABASE [TechSolutionsDB] SET ACCELERATED_DATABASE_RECOVERY = OFF   

GO 

ALTER DATABASE [TechSolutionsDB] SET QUERY_STORE = ON 

GO 

ALTER DATABASE [TechSolutionsDB] SET QUERY_STORE (OPERATION_MODE = READ_WRITE, CLEANUP_POLICY = (STALE_QUERY_THRESHOLD_DAYS = 30), DATA_FLUSH_INTERVAL_SECONDS = 900, INTERVAL_LENGTH_MINUTES = 60, MAX_STORAGE_SIZE_MB = 1000, QUERY_CAPTURE_MODE = AUTO, SIZE_BASED_CLEANUP_MODE = AUTO, MAX_PLANS_PER_QUERY = 200, WAIT_STATS_CAPTURE_MODE = ON) 

GO 

USE [TechSolutionsDB] 

GO 

/****** Object:  Table [dbo].[Clientes]    Script Date: 12/19/2023 8:23:28 PM ******/ 

SET ANSI_NULLS ON 

GO 

SET QUOTED_IDENTIFIER ON 

GO 

CREATE TABLE [dbo].[Clientes]( 

[ClienteID] [int] NOT NULL, 

[NombreCliente] [varchar](100) NULL, 

[Email] [varchar](100) NULL, 

PRIMARY KEY CLUSTERED  

( 

[ClienteID] ASC 

)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY] 

) ON [PRIMARY] 

GO 

/****** Object:  Table [dbo].[Empleados]    Script Date: 12/19/2023 8:23:28 PM ******/ 

SET ANSI_NULLS ON 

GO 

SET QUOTED_IDENTIFIER ON 

GO 

CREATE TABLE [dbo].[Empleados]( 

[EmpleadoID] [int] NOT NULL, 

[Nombre] [varchar](50) NULL, 

[Apellido] [varchar](50) NULL, 

[Cargo] [varchar](50) NULL, 

[Email] [varchar](100) NULL, 

PRIMARY KEY CLUSTERED  

( 

[EmpleadoID] ASC 

)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY] 

) ON [PRIMARY] 

GO 

/****** Object:  Table [dbo].[EmpleadoServicio]    Script Date: 12/19/2023 8:23:28 PM ******/ 

SET ANSI_NULLS ON 

GO 

SET QUOTED_IDENTIFIER ON 

GO 

CREATE TABLE [dbo].[EmpleadoServicio]( 

[EmpleadoID] [int] NOT NULL, 

[ServicioID] [int] NOT NULL, 

PRIMARY KEY CLUSTERED  

( 

[EmpleadoID] ASC, 

[ServicioID] ASC 

)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY] 

) ON [PRIMARY] 

GO 

/****** Object:  Table [dbo].[Proyectos]    Script Date: 12/19/2023 8:23:28 PM ******/ 

SET ANSI_NULLS ON 

GO 

SET QUOTED_IDENTIFIER ON 

GO 

CREATE TABLE [dbo].[Proyectos]( 

[ProyectoID] [int] NOT NULL, 

[NombreProyecto] [varchar](100) NULL, 

[LiderProyectoID] [int] NULL, 

PRIMARY KEY CLUSTERED  

( 

[ProyectoID] ASC 

)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY] 

) ON [PRIMARY] 

GO 

/****** Object:  Table [dbo].[Servicios]    Script Date: 12/19/2023 8:23:28 PM ******/ 

SET ANSI_NULLS ON 

GO 

SET QUOTED_IDENTIFIER ON 

GO 

CREATE TABLE [dbo].[Servicios]( 

[ServicioID] [int] NOT NULL, 

[NombreServicio] [varchar](100) NULL, 

PRIMARY KEY CLUSTERED  

( 

[ServicioID] ASC 

)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY] 

) ON [PRIMARY] 

GO 

INSERT [dbo].[Clientes] ([ClienteID], [NombreCliente], [Email]) VALUES (1, N'Cliente XYZ', N'info@clientexz.com') 

GO 

INSERT [dbo].[Empleados] ([EmpleadoID], [Nombre], [Apellido], [Cargo], [Email]) VALUES (1, N'Clady', N'German', N'Desarrolladora Senior', N'glady@gmail.com') 

INSERT [dbo].[Empleados] ([EmpleadoID], [Nombre], [Apellido], [Cargo], [Email]) VALUES (2, N'Carlos', N'Perez', N'Diseñador UI/UX', N'carlos@gmail.com') 

INSERT [dbo].[Empleados] ([EmpleadoID], [Nombre], [Apellido], [Cargo], [Email]) VALUES (3, N'Marta', N'Sosa', N'Especialista en Ciberseguridad', N'marta@gmail.com') 

GO 

INSERT [dbo].[EmpleadoServicio] ([EmpleadoID], [ServicioID]) VALUES (1, 1) 

INSERT [dbo].[EmpleadoServicio] ([EmpleadoID], [ServicioID]) VALUES (1, 4) 

INSERT [dbo].[EmpleadoServicio] ([EmpleadoID], [ServicioID]) VALUES (2, 2) 

INSERT [dbo].[EmpleadoServicio] ([EmpleadoID], [ServicioID]) VALUES (2, 5) 

INSERT [dbo].[EmpleadoServicio] ([EmpleadoID], [ServicioID]) VALUES (3, 3) 

INSERT [dbo].[EmpleadoServicio] ([EmpleadoID], [ServicioID]) VALUES (3, 6) 

GO 

INSERT [dbo].[Proyectos] ([ProyectoID], [NombreProyecto], [LiderProyectoID]) VALUES (1, N'Proyecto A', 1) 

GO 

INSERT [dbo].[Servicios] ([ServicioID], [NombreServicio]) VALUES (1, N'Desarrollo de Aplicaciones Móviles') 

INSERT [dbo].[Servicios] ([ServicioID], [NombreServicio]) VALUES (2, N'Inteligencia Artificial') 

INSERT [dbo].[Servicios] ([ServicioID], [NombreServicio]) VALUES (3, N'Ciberseguridad') 

INSERT [dbo].[Servicios] ([ServicioID], [NombreServicio]) VALUES (4, N'Educación Tecnológica') 

INSERT [dbo].[Servicios] ([ServicioID], [NombreServicio]) VALUES (5, N'Comercio Electrónico') 

INSERT [dbo].[Servicios] ([ServicioID], [NombreServicio]) VALUES (6, N'Dispositivos de Salud') 

GO 

ALTER TABLE [dbo].[EmpleadoServicio]  WITH CHECK ADD FOREIGN KEY([EmpleadoID]) 

REFERENCES [dbo].[Empleados] ([EmpleadoID]) 

GO 

ALTER TABLE [dbo].[EmpleadoServicio]  WITH CHECK ADD FOREIGN KEY([ServicioID]) 

REFERENCES [dbo].[Servicios] ([ServicioID]) 

GO 

ALTER TABLE [dbo].[Proyectos]  WITH CHECK ADD FOREIGN KEY([LiderProyectoID]) 

REFERENCES [dbo].[Empleados] ([EmpleadoID]) 

GO 

USE [master] 

GO 

ALTER DATABASE [TechSolutionsDB] SET  READ_WRITE  

GO 

 

