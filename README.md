# Resposta-Questao-1

using System;

public class ContaBancaria
{
    // Propriedades
    public int Numero { get; private set; }
    public string Titular { get; set; }
    public double Saldo { get; private set; }

    // Construtor
    public ContaBancaria(int numero, string titular, double depositoInicial = 0)
    {
        Numero = numero;
        Titular = titular;
        Saldo = depositoInicial;
    }

    // Método para depósito
    public void Depositar(double valor)
    {
        Saldo += valor;
    }

    // Método para saque (inclui taxa de $3.50)
    public void Sacar(double valor)
    {
        Saldo -= (valor + 3.50);
    }

    // Sobrescreve o método ToString para mostrar os dados da conta
    public override string ToString()
    {
        return $"Conta {Numero}, Titular: {Titular}, Saldo: $ {Saldo:F2}";
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Solicita os dados iniciais
        Console.Write("Entre o número da conta: ");
        int numeroConta = int.Parse(Console.ReadLine());

        Console.Write("Entre o titular da conta: ");
        string titularConta = Console.ReadLine();

        Console.Write("Haverá depósito inicial (s/n)? ");
        char resposta = char.Parse(Console.ReadLine());

        double depositoInicial = 0;
        if (resposta == 's' || resposta == 'S')
        {
            Console.Write("Entre o valor de depósito inicial: ");
            depositoInicial = double.Parse(Console.ReadLine());
        }

        // Criação da conta bancária
        ContaBancaria conta = new ContaBancaria(numeroConta, titularConta, depositoInicial);

        // Exibe os dados da conta
        Console.WriteLine("\nDados da conta:");
        Console.WriteLine(conta);

        // Realiza um depósito
        Console.Write("\nEntre um valor para depósito: ");
        double valorDeposito = double.Parse(Console.ReadLine());
        conta.Depositar(valorDeposito);

        // Exibe os dados atualizados da conta
        Console.WriteLine("\nDados da conta atualizados:");
        Console.WriteLine(conta);

        // Realiza um saque
        Console.Write("\nEntre um valor para saque: ");
        double valorSaque = double.Parse(Console.ReadLine());
        conta.Sacar(valorSaque);

        // Exibe os dados atualizados da conta
        Console.WriteLine("\nDados da conta atualizados:");
        Console.WriteLine(conta);
    }
}

