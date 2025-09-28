package curso;
/*
 * data: 27/09/25
 * Crie um programa que simula um jogo de adivinhação, que deve gerar um número aleatório entre 0 e 100 
 * e pedir para que o usuário tente adivinhar o número, em até 5 tentativas. 
 * A cada tentativa, o programa deve informar se o número digitado pelo usuário é maior ou menor do que o número gerado.
 */
import java.util.Random;
import java.util.Scanner;

public class JogoDeAdivinharFor {
	public static void main(String[] args) {
		Scanner entrada = new Scanner(System.in);
		
		//Variáveis Globais.
		String nomeUsuario;
		int numeroComputador, numeroUsuario = 0, numeroTentativas;
		int i = 0, cont = 0;
		
		//Computador escolhe seu número.
		numeroComputador = new Random().nextInt(100);
		System.out.println("Número escolhido pelo computador: "+numeroComputador);
		
		//Boas vindas ao jogador.
		System.out.println("******************** Seja Bem-Vindo ******************** ");
		System.out.println("****** Vamos Brincar no jogo de adivinhe o Número ******");
		System.out.println();
		
		//Usuário informa seu nome
		System.out.print("Informe seu nome: ");
		nomeUsuario = entrada.nextLine();
		
		//Usuário informa quantidade de tentativas.
		System.out.print("Informe o Número de jogadas para descobrir o número: ");
		numeroTentativas = Integer.parseInt(entrada.nextLine());
		
		//for para girar a quantidade de jogadas.
		for(i = 1; i <= numeroTentativas; i++) {
			cont += 1; //Iniciando a contagem de tentativas.
			
			System.out.println();
			System.out.println(cont+" Tentativa.");
			System.out.print("Escolha um número de 0 a 100: ");
			numeroUsuario = Integer.parseInt(entrada.nextLine());//Usuário escolhendo um número.
			
			if(numeroUsuario < 0 || numeroUsuario > 100) {//Usuário escolher um número fora do jogo.
				cont -= 1;//Não contar a jogada 
				i -= 1;
				System.out.println("Número escolhido é invalido...");
				System.out.println("Escolha um número entre 0 e 100");
			}
			else {//Entra no jogo.
				if(numeroUsuario == numeroComputador) {//Quando usuário acertar o número.
					System.out.println("************ Voçe acertou o Número ************");
					System.out.println("****** Parabéns, os número são iguais!!! ******");
					System.out.println("** O computador tinha escolhido o número: "+numeroComputador+" **");
					break;
				}else if(numeroUsuario > numeroComputador) {//Usuário escolher o número maior que o do computador.
					System.out.println(numeroUsuario+ "-> É maior...");
				}else if(numeroUsuario < numeroComputador) {//Usuário escolher o número menor que o do computador.
					System.out.println(numeroUsuario+ "-> É menor...");
				}
			}
		}//Final do For.
		if(numeroUsuario != numeroComputador) {//Quando acabar as tentativas.
			System.out.println();
			System.out.println("Suas tentativas acabaram...");
			System.out.println("O número escolhido pelo computador foi: "+numeroComputador);
		}		
		entrada.close();
	}//Main
}
