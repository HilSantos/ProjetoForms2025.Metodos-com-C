# Metodos-do-WinForms2025-com-C#
Atividades do ProjetoForms2025 usando Metodos com C#.

using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace ProjetoForms2025
{
    public partial class Metodos_com_C_ : Form
    {
        public Metodos_com_C_()
        {
            InitializeComponent();
        }

  private void btnCalcular_Click(object sender, EventArgs e)
        {
            // Verifica se o valor digitado é válido
            if (decimal.TryParse(txtValorMensal.Text, out decimal valorMensal))
            {
                // Calcula o valor anual (12 meses)
                decimal valorAnual = valorMensal * 12;

  // Exibe o resultado formatado como moeda
                lblResultado.Text = $"Resultado: R$ {valorAnual.ToString("N2")}";
            }
            else
            {
                // Se o valor digitado for inválido, exibe uma mensagem de erro
                MessageBox.Show("Por favor, digite um valor válido.", "Erro", 
                    MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
        }

  private void btnCalculo_Click(object sender, EventArgs e)
        {
            try
            {
                // Captura os valores digitados pelo usuário
                double distancia = Convert.ToDouble(txtDistancia.Text);
                double velocidadeMedia = Convert.ToDouble(txtVelocidadeMedia.Text);
                double consumoMedio = Convert.ToDouble(txtConsumoMedio.Text);

  // Calcula o tempo de viagem usando a classe Operacoes
                double tempoViagem = Operacoes.CalcularTempoViagem(distancia, velocidadeMedia);

  // Calcula o combustível necessário usando a classe Operacoes
                double combustivelNecessario = Operacoes.CalcularCombustivelNecessario(distancia, consumoMedio);

  // Exibe os resultados
                lblTempoViagem.Text = $"Tempo de Viagem: {tempoViagem.ToString("N2")} horas";
                lblCombustivelNecessario.Text = $"Combustível Necessário: {combustivelNecessario.ToString("N2")} litros";
            }
            catch (FormatException)
            {
                MessageBox.Show("Por favor, insira valores numéricos válidos.", "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
            catch (ArgumentException ex)
            {
                MessageBox.Show(ex.Message, "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
            catch (Exception ex)
            {
                MessageBox.Show("Ocorreu um erro inesperado: " + ex.Message, "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
        }

  private void btnCalcularDiferenca_Click(object sender, EventArgs e)
        {
            try
            {
                // Captura os horários digitados pelo usuário
                DateTime horarioInicial = DateTime.ParseExact(txtHorarioInicial.Text, "HH:mm", null);
                DateTime horarioFinal = DateTime.ParseExact(txtHorarioFinal.Text, "HH:mm", null);

  // Calcula a diferença entre os horários usando a classe Operacoes
                TimeSpan diferenca = Operacoes.CalcularDiferencaHorarios(horarioInicial, horarioFinal);

  // Exibe o resultado
                lblResultado.Text = $"Resultado: {diferenca.Hours} horas e {diferenca.Minutes} minutos";
            }
            catch (FormatException)
            {
                MessageBox.Show("Por favor, insira os horários no formato HH:mm.", "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
            catch (ArgumentException ex)
            {
                MessageBox.Show(ex.Message, "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
            catch (Exception ex)
            {
                MessageBox.Show("Ocorreu um erro inesperado: " + ex.Message, "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
        }

  private void btnConsumoMedio_Click(object sender, EventArgs e)
        {
            try
            {
                // Captura os valores digitados pelo usuário
                double distancia = Convert.ToDouble(txtDistancia.Text);
                double combustivelGasto = Convert.ToDouble(txtCombustivelGasto.Text);

  // Calcula o consumo médio usando a classe Operacoes
                double consumoMedio = Operacoes.CalcularConsumoMedio(distancia, combustivelGasto);

  // Exibe o resultado
                lblResultado.Text = $"Resultado: {consumoMedio.ToString("N2")} Km/L";
            }
            catch (FormatException)
            {
                MessageBox.Show("Por favor, insira valores numéricos válidos.", "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
            catch (ArgumentException ex)
            {
                MessageBox.Show(ex.Message, "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
            catch (Exception ex)
            {
                MessageBox.Show("Ocorreu um erro inesperado: " + ex.Message, "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
        }

  private void btnConverter_Click(object sender, EventArgs e)
        {
            try
            {
                // Captura o valor digitado pelo usuário
                double valorReais = Convert.ToDouble(txtValorReais.Text);

  // Verifica qual moeda foi selecionada
                if (rbDolar.Checked)
                {
                    // Converte para dólar usando a classe Operacoes
                    double valorConvertido = Operacoes.ConverterParaDolar(valorReais);
                    lblResultado.Text = $"Resultado: {valorConvertido.ToString("N2")} USD";
                }
                else if (rbEuro.Checked)
                {
                    // Converte para euro usando a classe Operacoes
                    double valorConvertido = Operacoes.ConverterParaEuro(valorReais);
                    lblResultado.Text = $"Resultado: {valorConvertido.ToString("N2")} EUR";
                }
                else
                {
                    MessageBox.Show("Selecione uma moeda para conversão.", "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
                }
            }
            catch (FormatException)
            {
                MessageBox.Show("Por favor, insira um valor numérico válido.", "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
            catch (ArgumentException ex)
            {
                MessageBox.Show(ex.Message, "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
            catch (Exception ex)
            {
                MessageBox.Show("Ocorreu um erro inesperado: " + ex.Message, "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
{

private RadioButton rbCelsiusParaFahrenheit;
private RadioButton rbFahrenheitParaCelsius;
private CheckBox cbSolDireto;

public Metodos2()
       {
           InitializeComponent();
           cbSolDireto = new CheckBox(); // Adicionando a inicialização do CheckBox
       }

private void btnCalcularIMC_Click(object sender, EventArgs e)
       {
           try
           {
               // Captura os valores digitados pelo usuário
               double peso = Convert.ToDouble(txtPeso.Text);
               double altura = Convert.ToDouble(txtAltura.Text);

// Calcula o IMC usando a classe Operacoes
               double imc = Operacoes.CalcularIMC(peso, altura);

// Exibe o resultado
               lblResultado.Text = $"Resultado: {imc.ToString("N2")}";
           }
           catch (FormatException)
           {
               MessageBox.Show("Por favor, insira valores numéricos válidos.", "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
           }
           catch (ArgumentException ex)
           {
               MessageBox.Show(ex.Message, "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
           }
           catch (Exception ex)
           {
               MessageBox.Show("Ocorreu um erro inesperado: " + ex.Message, "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
           }
       }

private string ClassificarIMC(double imc)
       {
           if (imc < 18.5)
               return "Abaixo do peso";
           else if (imc < 24.9)
               return "Peso normal";
           else if (imc < 29.9)
               return "Sobrepeso";
           else if (imc < 34.9)
               return "Obesidade Grau I";
           else if (imc < 39.9)
               return "Obesidade Grau II";
           else
               return "Obesidade Grau III";
       }

private void btnConversao_Click(object sender, EventArgs e)
       {
           try
           {
               // Captura o valor digitado pelo usuário
               double temperatura = Convert.ToDouble(txtTemperatura.Text);

// Verifica qual conversão foi selecionada
               if (rbCelsiusParaFahrenheit.Checked)
               {
                   // Converte Celsius para Fahrenheit usando a classe Operacoes
                   double resultado = Operacoes.CelsiusParaFahrenheit(temperatura);
                   lblResultado.Text = $"Resultado: {resultado.ToString("N2")} °F";
               }
               else if (rbFahrenheitParaCelsius.Checked)
               {
                   // Converte Fahrenheit para Celsius usando a classe Operacoes
                   double resultado = Operacoes.FahrenheitParaCelsius(temperatura);
                   lblResultado.Text = $"Resultado: {resultado.ToString("N2")} °C";
               }
               else
               {
                   MessageBox.Show("Selecione uma opção de conversão.", "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
               }
           }
           catch (FormatException)
           {
               MessageBox.Show("Por favor, insira um valor numérico válido.", "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
           }
           catch (Exception ex)
           {
               MessageBox.Show("Ocorreu um erro inesperado: " + ex.Message, "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
           }
       }

private void btnCalculoBTU_Click(object sender, EventArgs e)
       {
           try
           {
               // Captura os valores digitados pelo usuário
               double metragem = Convert.ToDouble(txtMetragem.Text);
               int pessoas = Convert.ToInt32(txtPessoas.Text);
               int eletronicos = Convert.ToInt32(txtEletronicos.Text);
               bool solDireto = cbSolDireto.Checked;

// Calcula a quantidade ideal de BTUs usando a classe Operacoes
               int btus = Operacoes.CalcularBTUs(metragem, pessoas, eletronicos, solDireto);

// Sugere o ar-condicionado ideal
               string sugestao = Operacoes.SugerirArCondicionado(btus);

// Exibe o resultado
               lblResultado.Text = $"Resultado: {btus} BTUs - Sugestão: {sugestao}";
           }
           catch (FormatException)
           {
               MessageBox.Show("Por favor, insira valores numéricos válidos.", "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
           }
           catch (ArgumentException ex)
           {
               MessageBox.Show(ex.Message, "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
           }
           catch (Exception ex)
           {
               MessageBox.Show("Ocorreu um erro inesperado: " + ex.Message, "Erro", MessageBoxButtons.OK, MessageBoxIcon.Error);
           }
       }
   }
}
