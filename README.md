[Хранение персональных данных согласно 152.docx](https://github.com/user-attachments/files/27309584/152.docx)
[Дамп.sql](https://github.com/user-attachments/files/27309586/default.sql)
CREATE DATABASE [ПерсональныеДанныеАД]
GO
USE [ПерсональныеДанныеАД]
GO
/****** Object:  DatabaseRole [admin]    Script Date: 03.05.2026 1:52:34 ******/
CREATE ROLE [admin]
GO
/****** Object:  DatabaseRole [archivist]    Script Date: 03.05.2026 1:52:34 ******/
CREATE ROLE [archivist]
GO
/****** Object:  DatabaseRole [operator_pdn]    Script Date: 03.05.2026 1:52:34 ******/
CREATE ROLE [operator_pdn]
GO
/****** Object:  DatabaseRole [security_officer]    Script Date: 03.05.2026 1:52:34 ******/
CREATE ROLE [security_officer]
GO
/****** Object:  DatabaseRole [user_basic]    Script Date: 03.05.2026 1:52:34 ******/
CREATE ROLE [user_basic]
GO
/****** Object:  Table [dbo].[Архив]    Script Date: 03.05.2026 1:52:34 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Архив](
	[Код] [int] NOT NULL,
	[КодСотрудника] [int] NULL,
	[КатегорияПерсональныхДанных] [nvarchar](150) NULL,
	[ДатаСоздания] [date] NULL,
	[ДатаПланируемогоУдаления] [date] NULL,
PRIMARY KEY CLUSTERED 
(
	[Код] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Аудит]    Script Date: 03.05.2026 1:52:34 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Аудит](
	[Код] [int] NOT NULL,
	[КодПользователя] [int] NULL,
	[НомерСотрудника] [int] NULL,
	[ТипДокумента] [nvarchar](250) NULL,
	[ДатаИВремя] [datetime] NULL,
	[Результат] [bit] NULL,
PRIMARY KEY CLUSTERED 
(
	[Код] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Должность]    Script Date: 03.05.2026 1:52:34 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Должность](
	[Код] [int] NOT NULL,
	[Название] [nvarchar](150) NULL,
PRIMARY KEY CLUSTERED 
(
	[Код] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Обезличивание]    Script Date: 03.05.2026 1:52:34 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Обезличивание](
	[Код] [int] NOT NULL,
	[Псевдоник] [nvarchar](225) NULL,
	[ВозростнаяГруппа] [nvarchar](150) NULL,
	[Отдел] [nvarchar](150) NULL,
PRIMARY KEY CLUSTERED 
(
	[Код] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[ПаспортныеДанные]    Script Date: 03.05.2026 1:52:34 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[ПаспортныеДанные](
	[Код] [int] NOT NULL,
	[Серия] [char](4) NULL,
	[Номер] [char](6) NULL,
	[ДатаВыдачи] [date] NULL,
	[КодСотрудника] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[Код] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[ПерсональныеДанные]    Script Date: 03.05.2026 1:52:34 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[ПерсональныеДанные](
	[Код] [int] NOT NULL,
	[фио] [nvarchar](225) NULL,
	[НомерТелефона] [char](18) NULL,
	[ЭлектроннаяПочта] [nvarchar](225) NULL,
	[КодСотрудника] [int] NULL,
	[СНИЛС] [char](9) NULL,
	[ИНН] [char](12) NULL,
PRIMARY KEY CLUSTERED 
(
	[Код] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Пользователь]    Script Date: 03.05.2026 1:52:34 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Пользователь](
	[Код] [int] NOT NULL,
	[Имя] [nvarchar](150) NULL,
PRIMARY KEY CLUSTERED 
(
	[Код] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Роль]    Script Date: 03.05.2026 1:52:34 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Роль](
	[Код] [int] NOT NULL,
	[Название] [nvarchar](150) NULL,
PRIMARY KEY CLUSTERED 
(
	[Код] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[РольПользователя]    Script Date: 03.05.2026 1:52:34 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[РольПользователя](
	[Код] [int] NOT NULL,
	[КодПользователя] [int] NULL,
	[КодРоли] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[Код] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Сотрудник]    Script Date: 03.05.2026 1:52:34 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Сотрудник](
	[Код] [int] NOT NULL,
	[КодДолжности] [int] NULL,
	[СтажРаботы] [char](8) NULL,
	[Статус] [bit] NULL,
PRIMARY KEY CLUSTERED 
(
	[Код] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
INSERT [dbo].[Архив] ([Код], [КодСотрудника], [КатегорияПерсональныхДанных], [ДатаСоздания], [ДатаПланируемогоУдаления]) VALUES (1, 1, N'Общие', CAST(N'2024-03-02' AS Date), CAST(N'2076-03-02' AS Date))
INSERT [dbo].[Архив] ([Код], [КодСотрудника], [КатегорияПерсональныхДанных], [ДатаСоздания], [ДатаПланируемогоУдаления]) VALUES (2, 2, N'Маркетенговые', CAST(N'2023-02-03' AS Date), CAST(N'2024-01-01' AS Date))
INSERT [dbo].[Архив] ([Код], [КодСотрудника], [КатегорияПерсональныхДанных], [ДатаСоздания], [ДатаПланируемогоУдаления]) VALUES (3, 3, N'Клиентские', CAST(N'2025-01-01' AS Date), CAST(N'2025-07-01' AS Date))
GO
INSERT [dbo].[Аудит] ([Код], [КодПользователя], [НомерСотрудника], [ТипДокумента], [ДатаИВремя], [Результат]) VALUES (1, 1, 1, N'Паспортные данные', CAST(N'2026-01-01T23:00:00.000' AS DateTime), 1)
INSERT [dbo].[Аудит] ([Код], [КодПользователя], [НомерСотрудника], [ТипДокумента], [ДатаИВремя], [Результат]) VALUES (2, 2, 3, N'Сотрудник', CAST(N'2026-01-02T12:30:00.000' AS DateTime), 1)
GO
INSERT [dbo].[Должность] ([Код], [Название]) VALUES (1, N'Менеджер')
INSERT [dbo].[Должность] ([Код], [Название]) VALUES (2, N'Системный администратор')
INSERT [dbo].[Должность] ([Код], [Название]) VALUES (3, N'Логист')
INSERT [dbo].[Должность] ([Код], [Название]) VALUES (4, N'Бугалтер')
INSERT [dbo].[Должность] ([Код], [Название]) VALUES (5, N'Офисный сотрудник')
GO
INSERT [dbo].[Обезличивание] ([Код], [Псевдоник], [ВозростнаяГруппа], [Отдел]) VALUES (1, N'ААА', N'25-30', N'Продажи')
INSERT [dbo].[Обезличивание] ([Код], [Псевдоник], [ВозростнаяГруппа], [Отдел]) VALUES (2, N'СВВ', N'20-30', N'Логистика')
INSERT [dbo].[Обезличивание] ([Код], [Псевдоник], [ВозростнаяГруппа], [Отдел]) VALUES (3, N'АДИ', N'20-25', N'Склад')
GO
INSERT [dbo].[ПаспортныеДанные] ([Код], [Серия], [Номер], [ДатаВыдачи], [КодСотрудника]) VALUES (1, N'4356', N'459876', CAST(N'2010-02-01' AS Date), 1)
INSERT [dbo].[ПаспортныеДанные] ([Код], [Серия], [Номер], [ДатаВыдачи], [КодСотрудника]) VALUES (2, N'0923', N'453287', CAST(N'2009-01-02' AS Date), 2)
INSERT [dbo].[ПаспортныеДанные] ([Код], [Серия], [Номер], [ДатаВыдачи], [КодСотрудника]) VALUES (3, N'6578', N'890765', CAST(N'2008-02-01' AS Date), 3)
GO
INSERT [dbo].[ПерсональныеДанные] ([Код], [фио], [НомерТелефона], [ЭлектроннаяПочта], [КодСотрудника], [СНИЛС], [ИНН]) VALUES (1, N'Аниеов Аник Аникович', N'7-(904)-999-99-99 ', N'Anicov@gmail.ru', 1, N'435654656', N'2435475786  ')
INSERT [dbo].[ПерсональныеДанные] ([Код], [фио], [НомерТелефона], [ЭлектроннаяПочта], [КодСотрудника], [СНИЛС], [ИНН]) VALUES (2, N'Смернов Василий Викторович', N'7-(654)-999-09-86 ', N'Smer3@gmail.com', 2, N'439239195', N'3495104504  ')
INSERT [dbo].[ПерсональныеДанные] ([Код], [фио], [НомерТелефона], [ЭлектроннаяПочта], [КодСотрудника], [СНИЛС], [ИНН]) VALUES (3, N'Алегов Дмитрий Игорьевич', N'7-(666)-999-66-66 ', N'Igor5@gmail.com', 3, N'323323433', N'3239876089  ')
GO
INSERT [dbo].[Пользователь] ([Код], [Имя]) VALUES (1, N'Вася')
INSERT [dbo].[Пользователь] ([Код], [Имя]) VALUES (2, N'Петя')
INSERT [dbo].[Пользователь] ([Код], [Имя]) VALUES (3, N'Вова')
INSERT [dbo].[Пользователь] ([Код], [Имя]) VALUES (4, N'Миша')
INSERT [dbo].[Пользователь] ([Код], [Имя]) VALUES (5, N'Гоша')
GO
INSERT [dbo].[Роль] ([Код], [Название]) VALUES (1, N'Администратор системы')
INSERT [dbo].[Роль] ([Код], [Название]) VALUES (2, N'Оператор персональных данных')
INSERT [dbo].[Роль] ([Код], [Название]) VALUES (3, N'Специалист по безопасности')
INSERT [dbo].[Роль] ([Код], [Название]) VALUES (4, N'Архиватор')
INSERT [dbo].[Роль] ([Код], [Название]) VALUES (5, N'Пользователь')
GO
INSERT [dbo].[Сотрудник] ([Код], [КодДолжности], [СтажРаботы], [Статус]) VALUES (1, 1, N'29 лет  ', 1)
INSERT [dbo].[Сотрудник] ([Код], [КодДолжности], [СтажРаботы], [Статус]) VALUES (2, 2, N'12 лет  ', 1)
INSERT [dbo].[Сотрудник] ([Код], [КодДолжности], [СтажРаботы], [Статус]) VALUES (3, 4, N'3 года  ', 1)
INSERT [dbo].[Сотрудник] ([Код], [КодДолжности], [СтажРаботы], [Статус]) VALUES (4, 1, N'13 лет  ', 1)
GO
ALTER TABLE [dbo].[Архив] ADD  CONSTRAINT [DF_ЗначениеПоУмолчанию]  DEFAULT ('Общие') FOR [КатегорияПерсональныхДанных]
GO
ALTER TABLE [dbo].[Архив]  WITH CHECK ADD  CONSTRAINT [FK_АрхивацияСотрудника] FOREIGN KEY([КодСотрудника])
REFERENCES [dbo].[Сотрудник] ([Код])
GO
ALTER TABLE [dbo].[Архив] CHECK CONSTRAINT [FK_АрхивацияСотрудника]
GO
ALTER TABLE [dbo].[Аудит]  WITH CHECK ADD  CONSTRAINT [FK_КодПользователяВАудите] FOREIGN KEY([КодПользователя])
REFERENCES [dbo].[Пользователь] ([Код])
GO
ALTER TABLE [dbo].[Аудит] CHECK CONSTRAINT [FK_КодПользователяВАудите]
GO
ALTER TABLE [dbo].[ПаспортныеДанные]  WITH CHECK ADD  CONSTRAINT [FK_ПаспортСотрудника] FOREIGN KEY([КодСотрудника])
REFERENCES [dbo].[Сотрудник] ([Код])
GO
ALTER TABLE [dbo].[ПаспортныеДанные] CHECK CONSTRAINT [FK_ПаспортСотрудника]
GO
ALTER TABLE [dbo].[ПерсональныеДанные]  WITH CHECK ADD  CONSTRAINT [FK_ПерсональныеДанныеКодСотрудника] FOREIGN KEY([КодСотрудника])
REFERENCES [dbo].[Сотрудник] ([Код])
GO
ALTER TABLE [dbo].[ПерсональныеДанные] CHECK CONSTRAINT [FK_ПерсональныеДанныеКодСотрудника]
GO
ALTER TABLE [dbo].[РольПользователя]  WITH CHECK ADD  CONSTRAINT [FK_КодПользователя_Пользователь] FOREIGN KEY([КодПользователя])
REFERENCES [dbo].[Пользователь] ([Код])
GO
ALTER TABLE [dbo].[РольПользователя] CHECK CONSTRAINT [FK_КодПользователя_Пользователь]
GO
ALTER TABLE [dbo].[РольПользователя]  WITH CHECK ADD  CONSTRAINT [FK_КодРоли_Роль] FOREIGN KEY([КодРоли])
REFERENCES [dbo].[Роль] ([Код])
GO
ALTER TABLE [dbo].[РольПользователя] CHECK CONSTRAINT [FK_КодРоли_Роль]
GO
ALTER TABLE [dbo].[Сотрудник]  WITH CHECK ADD  CONSTRAINT [FK_КодДолжности] FOREIGN KEY([КодДолжности])
REFERENCES [dbo].[Должность] ([Код])
GO
ALTER TABLE [dbo].[Сотрудник] CHECK CONSTRAINT [FK_КодДолжности]
GO
ALTER TABLE [dbo].[ПаспортныеДанные]  WITH CHECK ADD  CONSTRAINT [CK_ПолнаяСерияПаспорта] CHECK  ((len([Серия])=(4)))
GO
ALTER TABLE [dbo].[ПаспортныеДанные] CHECK CONSTRAINT [CK_ПолнаяСерияПаспорта]
GO
ALTER TABLE [dbo].[ПаспортныеДанные]  WITH CHECK ADD  CONSTRAINT [CK_ПолныйНомерПаспорта] CHECK  ((len([Номер])=(6)))
GO
ALTER TABLE [dbo].[ПаспортныеДанные] CHECK CONSTRAINT [CK_ПолныйНомерПаспорта]
GO
ALTER TABLE [dbo].[ПерсональныеДанные]  WITH CHECK ADD  CONSTRAINT [CK_ВведеныВсеЗначенияВСнилс] CHECK  ((len([СНИЛС])=(9)))
GO
ALTER TABLE [dbo].[ПерсональныеДанные] CHECK CONSTRAINT [CK_ВведеныВсеЗначенияВСнилс]
GO
ALTER TABLE [dbo].[ПерсональныеДанные]  WITH CHECK ADD  CONSTRAINT [CK_ИНННеменьшедесятиСимволов] CHECK  ((len([ИНН])>=(10)))
GO
ALTER TABLE [dbo].[ПерсональныеДанные] CHECK CONSTRAINT [CK_ИНННеменьшедесятиСимволов]
GO
