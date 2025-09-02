class Funcionario {
  #salario;

  constructor(nome, cpf, salario) {
    if (new.target===Funcionario) {
      throw new Error("A classe abstrata 'Funcionario' não pode ser instanciada diretamente.");
    }

    this.nome = nome;
    this.cpf = cpf;
    this.setSalario(salario); 
  }

  getSalario() {
    return this.#salario;
  }

  setSalario(valor) {
    if (typeof valor !== 'number' || valor < 0) {
      throw new Error("Salário deve ser um número positivo.");
    }
    this.#salario = valor;
  }

  descreverFuncao() {
    throw new Error("O método abstrato 'descreverFuncao()' deve ser implementado pela subclasse.");
  }
}

/* ---------------------------------------------------------------------------------------------------- */

class Especialidade {
  constructor(nome) {
    this.nome =nome;
  }

  toString() {
    return this.nome;
  }
}

/* ---------------------------------------------------------------------------------------------------- */

class Agenda {
  constructor(data, descricao, responsavel) {
    this.data = new Date(data);
    this.descricao= descricao;
    this.responsavel = responsavel; 
  }

  resumo() {
    return `Agenda: ${this.descricao} em ${this.data.toLocaleString()} (Responsável: ${this.responsavel})`;
  }
}

/* ---------------------------------------------------------------------------------------------------- */

class Medico extends Funcionario {
  constructor(nome, cpf, salario) {
    super(nome, cpf, salario);
    this.especialidades = []; 
  }

  descreverFuncao() {
    return `${this.nome} é médico.`;
  }

  adicionarEspecialidade(especialidade) {
    if (!(especialidade instanceof Especialidade)) {
      throw new Error("Parâmetro deve ser uma instância de Especialidade.");
    }
    this.especialidades.push(especialidade);
  }

  listarEspecialidades() {
    return this.especialidades.map(e => e.toString()).join(", ");
  }
}

/* ---------------------------------------------------------------------------------------------------- */

class Secretaria extends Funcionario {
  constructor(nome, cpf, salario) {
    super(nome, cpf, salario);
    this.agendas = []; 
  }

  descreverFuncao() {
    return `${this.nome} é a secretária.`;
  }

  criarAgenda(data, descricao, responsavel) {
    const novaAgenda = new Agenda(data, descricao, responsavel);
    this.agendas.push(novaAgenda);
  }

  listarAgendas() {
    return this.agendas.map(a => a.resumo()).join("\n");
  }
}

/* ---------------------------------------------------------------------------------------------------- */

const neuro = new Especialidade("Neurologia");

const drPaulo = new Medico("Dr. Paulo", "123.456.789-10", 30000);
drPaulo.adicionarEspecialidade(neuro);

console.log(drPaulo.descreverFuncao());
console.log("Especialidades:", drPaulo.listarEspecialidades());

const rosa = new Secretaria("Rosa", "987.654.321-10", 4500);
rosa.criarAgenda("2025-09-03, 09:30:00", "Organizar prontuários", "Rosa");
rosa.criarAgenda("2025-09-03, 11:00:00", "Consulta Médica com Luis", "Dr. Paulo");

console.log(rosa.descreverFuncao());
console.log(rosa.listarAgendas());
