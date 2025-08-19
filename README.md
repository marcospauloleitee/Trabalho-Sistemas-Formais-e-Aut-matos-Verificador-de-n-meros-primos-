# Trabalho-Sistemas-Formais-e-Aut-matos-Verificador-de-n-meros-primos-

package tenet;

import java.util.Scanner;

public class SistemasAutomatos {
    
    // Função para verificar se um número é primo
    public static boolean ehPrimo(int numero) {
        // Números menores ou iguais a 1 não são primos
        if (numero <= 1) {
            return false;
        }
        
        // 2 é o único número par primo
        if (numero == 2) {
            return true;
        }
        
        // Números pares maiores que 2 não são primos
        if (numero == 2) {
            return true; // 2 é o único número par primo
        }

        if (numero % 2 == 0) {
            return false; // todos os outros pares não são primos
        }
        
        // Verifica divisores ímpares até a raiz quadrada do número 
        //não precisamos checar todos os números até numero.
        //Por quê? Se um número tem um divisor maior que sua raiz quadrada, ele 
        //obrigatoriamente terá um divisor menor que a raiz também.
        //i += 2 adiciona de 2 em 2 no divisor pra verificar até a raiz quadrada se ha divisão exata do dividendo
        for (int i = 3; i <= Math.sqrt(numero); i += 2) {
            if (numero % i == 0) {
                return false; // Encontrou um divisor, não é primo
            }
        }
        
        return true; // Não encontrou divisores, é primo
    }
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("🔢 VERIFICADOR DE NÚMEROS PRIMOS");
        System.out.println("Digite um número inteiro positivo (ou -1 para sair):");
        
        while (true) {
            System.out.print("\n>>> Digite um número: ");
            int numero = scanner.nextInt();
            
            if (numero == -1) {
                break;
            }
            
            if (ehPrimo(numero)) {
                System.out.println("✅ " + numero + " é um número PRIMO!");
            } else {
                System.out.println("❌ " + numero + " NÃO é primo.");
            }
        }
        
        scanner.close();
        System.out.println("\nPrograma encerrado. Obrigado!");
    }
}	

