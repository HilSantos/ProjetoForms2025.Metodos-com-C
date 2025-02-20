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
        }
    }
}
