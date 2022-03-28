from bs4 import BeautifulSoup
from urllib.request import Request, urlopen
import random

class Jogos:
    def __init__(self):
        num_pag_aleatoria = random.randint(0, 192)
        pag_aleatoria = f"https://www.metacritic.com/browse/games/score/metascore/all/all/filtered?page" \
                          f"={num_pag_aleatoria}"

        hdr = {'User-Agent': 'Mozilla/5.0'}
        req = Request(pag_aleatoria, headers=hdr)
        page = urlopen(req)
        soup = BeautifulSoup(page, features="html.parser")

        num_jog_aleatorio = random.randint(1, 100)

        self.nome = soup.select('a.title')[num_jog_aleatorio].text.strip()
        self.rating = float(soup.select('a.metascore_anchor')[num_jog_aleatorio].text.strip())
        self.plat = soup.select('span.data')[num_jog_aleatorio].text.strip()

highest_score = 0

while True:

    score = 0
    print('Começando novo jogo...')

    with open('HOLG.txt', 'w'):
        pass

    y = True
    while y == True:
        print('-' * 28)
        print(f'\33[33mPontuação: {score}')
        print(f'Maior pontuação: {highest_score}\33[m')
        print('Aguarde enquanto pegamos os dados...')
        print('-' * 28)

        try:
            if score < 1:
                jogo1 = Jogos()
                jogo1_nome = jogo1.nome
                jogo1_plat = jogo1.plat
                jogo1_rating = str(jogo1.rating)

            jogo2 = Jogos()

        except:
            print('\33[31mSentimos muito, houve um erro inesperado. Para não te prejudicar vamos lhe dar o '
                  'mesmo jogo! ;) \33[m')

        with open('HOLG.txt', 'a') as dados:
            dados.write(f'{jogo2.nome}/')
            dados.write(f'{jogo2.plat}/')
            dados.write(f'{str(jogo2.rating)}\n')

        print(jogo2.rating)

        if len(jogo1_nome) <= 5:
            escala = 32
        else:
            escala = 20

        print(jogo1_nome, jogo2.nome, sep=' ' * escala)

        print(f'Plataforma: {jogo1_plat}', f'Plataforma: {jogo2.plat}',
              sep= (' ' * ((escala + len(jogo1_nome)) - (12 + len(jogo1_plat)) )))

        print(f'MetaCritic Score: \33[32m{jogo1_rating}\33[m', f'MetaCritic Score: \33[32m-\33[m ',
              sep= (' ' * (escala + len(jogo1_nome) - (18 + len(jogo1_rating)) )))

        print()
        print('1 - MAIOR')
        print('2 - MENOR')
        print()

        x = True
        while x == True:
            try:
                resposta = int(input('Resposta (1 ou 2): '))
                if resposta not in [1, 2]:
                    print('Resposta inválida, número precisa ser 1 (Maior) ou 2 (Menor)')
                if resposta == 1:
                    if float(jogo1_rating) <= jogo2.rating:
                        print('\33[32mCorreto!')
                        print(f'A pontuação de {jogo2.nome} era: {jogo2.rating}\33[m')
                        score += 1
                        x = False
                    else:
                        print('\33[31mIncorreto, mas não desista!')
                        print(f'A pontuação de {jogo2.nome} era: {jogo2.rating}\33[m')
                        x = False
                        y = False
                if resposta == 2:
                    if float(jogo1_rating) >= jogo2.rating:
                        print('\33[32mCorreto!')
                        print(f'A pontuação de {jogo2.nome} era: {jogo2.rating}\33[m')
                        score += 1
                        x = False
                    else:
                        print('\33[31mIncorreto, mas não desista!')
                        print(f'A pontuação de {jogo2.nome} era: {jogo2.rating}\33[m')
                        x = False
                        y = False
            except ValueError as error:
                print(f'Erro ao introduzir resposta, o valor aplicado não é um número inteiro: {error}')

        if score >= 1:
            with open('HOLG.txt', 'r') as dados:
                linhas = dados.read().splitlines()
                ultima_linha = linhas[-1]
                info = ultima_linha.split('/')

                jogo1_nome = info[0]
                jogo1_plat = info[1]
                jogo1_rating = info[2]

        if score > highest_score:
            highest_score = score
