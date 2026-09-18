-- Criando um novo Banco de Dados
CREATE DATABASE BD_ACADEMICO;

-- instanciando (executando o BD_ACADEMICO
USE BD_ACADEMICO;

-- Criando a tabela curso
CREATE TABLE CURSO
(
	co_curso	int		not null,
    nome		varchar(40)	null
);
-- Esqueci de incluir a chave-primária
-- então iremos alterar esta table incluindo
-- uma restrição (constraint) de primary key
alter table CURSO add constraint PK_CURSO primary key (co_curso);

-- Criando a tabela TURMA
create table TURMA
(
	co_turma		char(11)		not null,
    ano				char(4)			null,
    periodo			char(1)			null,
    descricao		char(50)		null,
    dt_inicial		datetime		null,
    dt_final		datetime		null,
    num_provas		int				null,
    co_curso		int				null
);

alter table TURMA add constraint PK_TURMA primary key (co_turma);

alter table TURMA add constraint FK_TURMA_CURSO foreign key (co_curso) references CURSO(co_curso);

create table ALUNO
(
	co_aluno		int				not null,
    dt_nascimento	datetime		null,
    sg_sexo			char(1)			null,
    nome			varchar(20)		null,
    co_estadocivil	char(1)			null,
    no_pai			varchar(70)		null,
    no_mae			varchar(70)		null
);
alter table ALUNO add constraint PK_ALUNO primary key (co_aluno);

create table ALUNO_TURMA
(
	co_aluno		int				not null,
    co_turma		char(11)		not null,
    dt_matricula	datetime		null,
    dt_cancelamento	datetime		null
);
alter table ALUNO_TURMA add constraint PK_ALUNO_TURMA primary key (co_aluno, co_turma);
alter table ALUNO_TURMA add constraint FK_ALUNO_TURMA_ALUNO foreign key (co_aluno) 
references ALUNO(co_aluno);
alter table ALUNO_TURMA add constraint FK_ALUNO_TURMA_TURMA foreign key (co_turma)
references TURMA (co_turma);

create table PROFESSOR 
(
	co_professor	int				not null,
    sg_sexo			char(1)			null,
    nome			varchar(20)		null,
    dt_nascimento	datetime		null
);
alter table PROFESSOR add constraint PK_PROFESSOR primary key (co_professor);

create table DISCIPLINA
(
	co_disciplina		char(2)		not null,
    no_disciplina		varchar(30)	null
);
alter table DISCIPLINA add constraint PK_DISCIPLINA primary key (co_disciplina);

create table PROF_TURM_DISC
(
	co_professor	int				not null,
    co_turma		char(11)		not null,
    co_disciplina	char(2)			not null
);
alter table PROF_TURM_DISC add constraint PK_PROF_TURM_DISC primary key (co_professor, co_turma, co_disciplina);

alter table PROF_TURM_DISC add constraint FK_PROF_TURM_DISC_PROFESSOR foreign key (co_professor) 
references PROFESSOR(co_professor);

alter table PROF_TURM_DISC add constraint FK_PROF_TURM_DISC_TURMA foreign key (co_turma) 
references TURMA(co_turma);

alter table PROF_TURM_DISC add constraint FK_PROF_TURM_DISC_DISCIPLINA foreign key (co_disciplina)
references DISCIPLINA(co_disciplina);

create table PROVA
(
	co_prova		char(3)			not null,
    ds_prova		varchar(20)		null
);
alter table PROVA add constraint PK_PROVA primary key (co_prova);

create table AVALIACAO
(
	co_aluno		int				not null,
    co_turma		char(11)		not null,
    co_disciplina 	char(2)			not null,
    co_prova		char(3)			not null,
    dt_avaliacao	datetime		null,
    nt_avaliacao	float(53)		null
);
alter table AVALIACAO add constraint PK_AVALIACAO primary key (co_aluno, co_turma, co_disciplina, co_prova);

alter table AVALIACAO add constraint FK_AVALIACAO_ALUNO foreign key (co_aluno)
references ALUNO(co_aluno);

alter table AVALIACAO add constraint FK_AVALIACAO_TURMA foreign key (co_turma)
references TURMA(co_turma);

alter table AVALIACAO add constraint FK_AVALIACAO_DISCIPLINA foreign key (co_disciplina)
references DISCIPLINA(co_disciplina);

alter table AVALIACAO add constraint FK_AVALIACAO_PROVA foreign key (co_prova)
references PROVA(co_prova);

create table FREQUENCIA
(
	co_aluno		int				not null,
    co_turma		char(11)		not null,
    co_disciplina	char(2)			not null,
    dt_frequencia	datetime		not null,
    frequencia 		char(1)			null
);
alter table FREQUENCIA add constraint PK_FREQUENCIA primary key (co_aluno, co_turma, co_disciplina, dt_frequencia);

alter table FREQUENCIA add constraint FK_FREQUENCIA_ALUNO foreign key (co_aluno)
references ALUNO(co_aluno);

alter table FREQUENCIA add constraint FK_FREQUENCIA_TURMA foreign key (co_turma)
references TURMA(co_turma);

alter table FREQUENCIA add constraint FK_FREQUENCIA_DISCIPLINA foreign key (co_disciplina)
references DISCIPLINA(co_disciplina);

