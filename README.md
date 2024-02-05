# Modulo 16
Conteudo de apoio: 

# Exercicio
## Injeção de Dependências

### O que é
O padrão de projeto "Injeção de Dependências" (Dependency Injection, em inglês) é um princípio de design de software que visa promover a desacoplagem entre componentes e tornar o código mais flexível, testável e fácil de manter. Em Java, a Injeção de Dependências pode ser implementada de várias maneiras, sendo a Injeção de Dependências por meio de construtor, método ou propriedade uma das abordagens mais comuns.

A ideia básica da Injeção de Dependências é que uma classe não deve ser responsável por criar as instâncias de suas dependências, mas sim recebê-las de uma fonte externa. Isso pode ser feito por meio de um framework de Injeção de Dependências, como Spring, Guice, Dagger, entre outros, ou manualmente.

### Exemplo:

        // Interface da dependência
        interface ServicoNotificacao {
            void notificar(String mensagem);
        }
        
        // Implementação da dependência
        class ServicoNotificacaoEmail implements ServicoNotificacao {
            @Override
            public void notificar(String mensagem) {
                System.out.println("Notificação por e-mail: " + mensagem);
            }
        }
        
        // Classe que recebe a dependência por meio do construtor (Injeção de Dependências)
        class Cliente {
            private final ServicoNotificacao servicoNotificacao;
        
            // Construtor que recebe a dependência
            public Cliente(ServicoNotificacao servicoNotificacao) {
                this.servicoNotificacao = servicoNotificacao;
            }
        
            public void realizarAcao() {
                // ... lógica da classe Cliente ...
        
                // Utilização da dependência
                servicoNotificacao.notificar("Ação realizada com sucesso!");
            }
        }
        
        // Exemplo de utilização
        public class Main {
            public static void main(String[] args) {
                // Criação da instância da implementação da dependência
                ServicoNotificacao servicoNotificacao = new ServicoNotificacaoEmail();
        
                // Criação da instância da classe Cliente, passando a dependência por meio do construtor
                Cliente cliente = new Cliente(servicoNotificacao);
        
                // Execução da ação
                cliente.realizarAcao();
            }
        }
Neste exemplo, a classe Cliente depende de um serviço de notificação, e essa dependência é injetada por meio do construtor. Isso torna a classe Cliente mais flexível, pois permite a substituição fácil da implementação do ServicoNotificacao sem modificar o código da classe Cliente.

Frameworks de Injeção de Dependências, como o Spring, tornam esse processo ainda mais automatizado e oferecem recursos adicionais, como gerenciamento de ciclo de vida, injeção por anotações, e configuração por meio de arquivos de contexto.
