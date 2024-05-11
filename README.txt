# imersao_ia_gemini
Projeto de Imersão de IA - ComaBemAI

1-) Descrição do Projeto:

Trata-se de um projeto desenvolvido por mim durante a Imersão de IA sobre o Gemini, oferecido pela parceria da
Google, Alura e da FIAP. O ComaBemAI, é um software que interage com um usuário num contexto discontraído e
informativo, captando informações do cliente (dados do usuário) com o objetivo de retornar um plano alimentar
personalizado.

2-) Objetivo detalhado do Projeto:

Por meio de uma interface simples, amigável e informativa, captar dados pessoais, biológicos e preferências do
usuário, processar esses dados através de algumas fórmulas e conceitos de nutrição e nutrologia para construir
um "prompt" para a IA (inteligência artificial) Gemini gerar um Plano Alimentar Personalizado ao cliente.

3-) Ambiente e linguagem de programação:

O projeto foi desenvolvido na linguagem Python, no ambiente Jupyter Notebook, com integração de bibliotecas de
ia gemini da Google, na plataforma de nuvem Colab da Google.

4-) Arquivos:

ComaBemIA.ipynb : código fonte
README.md       : esta documentação

5-) Variáveis relativas aos Dados do Usuário

    nm_usuario :                        nome do usuário / como o usuário gostaria de ser chamado
    peso_usuario :                      peso corpóreo (em kg)
    altura_usuario :                    altura (em metros)
    idade_usuario :                     idade atual (em anos)
    genero_usuario :                    gênero biológico (M para mulher e H para homem)
    multiplicador_atividade_usuario     pontuação do nível de atividade física conforme tabela apresentada
    imc_usuario                         IMC (índice de massa corporal) *
    classificacao_imc_usuario           classificação do IMC
    tmb_usuario                         TMB (taxa metabólica basal *)
    get_usuario                         GET (gasto energético total *)
    tp_plano_usuario                    objetivo do usuário (ganhar ou perder peso)
    qt_kcal_plano_usuario               quantidade de calorias do plano alimentar do usuário *
    qtd_calorias_proteina               quantidade de calorias referente a proteínas *
    qtd_calorias_carboidrato            quantidade de calorias referente a carboidrato *
    qtd_calorias_lipideos               quantidade de calorias referente a lipídeos *
    qtd_gramas_fibras_plano_usuario     quantidade de fibras no plano alimentar   
    lista_alimentos_recusados_usuario   lista de alimentos indesejados pelo usuário
    lista_alimentos_alergenicos_usuario lista de alimentos alergênicos ao usuário
    refeicoes_semana_usuario            configuração das refeições de segunda a sexta-feira
    refeicoes_finaldesemana_usuario     configuração das refeições no sábado e domingo

6-) Fórmulas Utilizadas (*):

a-) Para cálculo da TMB (Taxa Metabólica Basal): 

    Fórmula de Harris Benedict:

    Para gênero biológico masculino: TMB = 66,5 + (13,75 x peso em kg) + (5 x altura em cm) - (6,75 x idade em anos)
    Para gênero biológico feminino:  TMB = 655,1 + (9,563 x peso em kg) + (1,85 x altura em cm) - (4,676 x idade em anos)

b-) Para cálculo do IMC (Índice de Massa Corpórea):
    IMC = peso (em kg) / (altura (em metros) x altura (em metros))

c-) GET (Gasto Energético Total):
    GET = TBM x fator multiplicador de atividade física ( ... a variável multiplicador_atividade_usuario)

d-) Quantidade de calorias do plano alimentar do usuário
    
    Se o objetivo do usuário é ganhar peso (consideramos massa magra) : 
    qt_kcal_plano_usuario = GET + 500 kcal

    Se o objetivo do usuário é perder peso (consideramos massa gorda) : 
    qt_kcal_plano_usuario = GET - 750 kcal   

e-) Quantidade de calorias referente as proteínas:

    Se o objetivo do usuário é ganhar peso (consideramos massa magra) : 
    qtd_calorias_proteina = peso_usuario * 2.5 (gramas de proteína) * 4 (quantidade de kcal por grama de proteína)

    Se o objetivo do usuário é perder peso (consideramos massa gorda) : 
    qtd_calorias_proteina = peso_usuario * 1 (grama de proteína) * 4 (quantidade de kcal por grama de proteína)

f-) Quantidade de calorias referente a carboidratos:

    Se o objetivo do usuário é ganhar peso (consideramos massa magra) : 
    qtd_calorias_carboidrato = qt_kcal_plano_usuario - qtd_calorias_lipideos - qtd_calorias_proteina

    Se o objetivo do usuário é perder peso (consideramos massa gorda) : 
    qtd_calorias_carboidrato = peso_usuario * 1 (grama de carboidrato) * 4 (quantidade de kcal por grama de carboidrato)

g-) Quantidade de calorias referente a lipídeos:

    Se o objetivo do usuário é ganhar peso (consideramos massa magra) : 
    qtd_calorias_lipideos = 0.2 * qt_kcal_plano_usuario (20% da qt_kcal_plano_usuario)

    Se o objetivo do usuário é perder peso (consideramos massa gorda) : 
    qtd_calorias_lipideos = qt_kcal_plano_usuario - qtd_calorias_proteina - qtd_calorias_carboidrato

i-) Quantidade de fibras no plano alimentar:

    Se homem : qtd_gramas_fibras_plano_usuario = 34 (gramas de fibras)
    Se mulher: qtd_gramas_fibras_plano_usuario = 25 (gramas de fibras)






