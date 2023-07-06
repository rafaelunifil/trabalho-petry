ListaProdutos 
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class ListaProdutos {

    public static class Produto {
        private String nome;
        private int quantidade;
        private float valor;

        public Produto(String nome, int quantidade, float valor) {
            this.nome = nome;
            this.quantidade = quantidade;
            this.valor = valor;
        }

        public String getNome() {
            return nome;
        }

        public int getQuantidade() {
            return quantidade;
        }

        public float getValor() {
            return valor;
        }
    }

    public static List<Produto> lista = new ArrayList<>();

    public static void inserirProduto() {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Insira o nome do produto: ");
        String nome = scanner.nextLine();

        System.out.println("Insira a quantidade de produtos: ");
        int quantidade = scanner.nextInt();

        System.out.println("Insira o valor do produto: ");
        float valor = scanner.nextFloat();

        Produto produto = new Produto(nome, quantidade, valor);
        lista.add(produto);

        System.out.println("Produto adicionado.");
    }

    public static void mostrarProdutos() {
        System.out.println("Produtos na lista:");

        for (Produto produto : lista) {
            System.out.println("Nome: " + produto.getNome());
            System.out.println("Quantidade: " + produto.getQuantidade());
            System.out.println("Valor: " + produto.getValor());
            System.out.println();
        }
    }

    public static void calcularValor() {
        float valorFinal = 0.0f;

        for (Produto produto : lista) {
            valorFinal += produto.getQuantidade() * produto.getValor();
        }

        System.out.println("Valor final da lista de compras: " + valorFinal + " R$");
    }

    public static void removerProduto(String nomeProduto) {
        boolean encontrado = false;

        for (int i = 0; i < lista.size(); i++) {
            Produto produto = lista.get(i);

            if (produto.getNome().equals(nomeProduto)) {
                encontrado = true;
                lista.remove(i);
                break;
            }
        }

        if (encontrado) {
            System.out.println("Produto removido.");
        } else {
            System.out.println("Produto não encontrado.");
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int opcao;
        String nomeProduto;

        do {
            System.out.println("Escolha uma opção: ");
            System.out.println("1 - Mostrar lista de compras.");
            System.out.println("2 - Inserir produto na lista de compras.");
            System.out.println("3 - Calcular valor dos produtos da lista de compras.");
            System.out.println("4 - Remover produto da lista de compras.");
            System.out.println("0 - Sair.");

            opcao = scanner.nextInt();
            scanner.nextLine(); // Consume newline character

            switch (opcao) {
                case 0:
                    break;
                case 1:
                    mostrarProdutos();
                    break;
                case 2:
                    inserirProduto();
                    break;
                case 3:
                    calcularValor();
                    break;
                case 4:
                    System.out.println("Insira o nome do produto a ser removido:");
                    nomeProduto = scanner.nextLine();
                   removerProduto(nomeProduto);
                    break;
                default:
                    System.out.println("Opção inválida! Escolha novamente.");
            }
        } while (opcao != 0);
    }
}
