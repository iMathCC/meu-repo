# meu-repo

alguma coisa

==========================================
​A. Compre uma pá (Força Bruta)
​==========================================
​custo_pa, valor_moeda_especial = map(int, input().split())
quantidade_pas = 1
while True:
valor_total = quantidade_pas * custo_pa
if valor_total % 10 == 0 or (valor_total - valor_moeda_especial) % 10 == 0:
break
quantidade_pas += 1
print(quantidade_pas)
​==========================================
​B. Viagem Barata (Força Bruta)
​==========================================
​viagens_necessarias, viagens_especial, preco_simples, preco_especial = map(int, input().split())
menor_custo = viagens_necessarias * preco_simples
for quantidade_especial in range(viagens_necessarias + 1):
viagens_cobertas = quantidade_especial * viagens_especial
custo_atual = quantidade_especial * preco_especial
if viagens_cobertas < viagens_necessarias:
viagens_restantes = viagens_necessarias - viagens_cobertas
custo_atual += viagens_restantes * preco_simples
if custo_atual < menor_custo:
menor_custo = custo_atual
print(menor_custo)
​==========================================
​C. Maiúsculas e Minúsculas (Backtracking)
​==========================================
​def gerar_combinacoes(indice, string_atual, lista_resultado):
if indice == len(string_original):
lista_resultado.append(string_atual)
return
caractere = string_original[indice]
if caractere.isalpha():
gerar_combinacoes(indice + 1, string_atual + caractere.lower(), lista_resultado)
gerar_combinacoes(indice + 1, string_atual + caractere.upper(), lista_resultado)
else:
gerar_combinacoes(indice + 1, string_atual + caractere, lista_resultado)
​string_original = input().strip()
resultado = []
gerar_combinacoes(0, "", resultado)
print(resultado)
​==========================================
​D. Restaurar Endereços IP (Backtracking)
​==========================================
​def validar_parte(parte):
if len(parte) > 1 and parte[0] == '0':
return False
return 0 <= int(parte) <= 255
​def fazer_backtracking(indice_atual, partes_atuais):
if len(partes_atuais) == 4:
if indice_atual == len(string_digitos):
lista_ips.append(".".join(partes_atuais))
return
​for tamanho in range(1, 4):
if indice_atual + tamanho <= len(string_digitos):
parte = string_digitos[indice_atual:indice_atual + tamanho]
if validar_parte(parte):
fazer_backtracking(indice_atual + tamanho, partes_atuais + [parte])
​string_digitos = input().strip()
lista_ips = []
fazer_backtracking(0, [])
print(lista_ips)