import time

class FazendaSustentavel:
    def __init__(self, nome, area_hectares):
        self.nome = nome
        self.area = area_hectares
        self.producao_estimada = 0  # em toneladas
        self.uso_agua = 0           # em litros por quilo produzido
        self.uso_fertilizantes = 0  # em kg por hectare
        
    def monitorar_safra(self, producao, agua, fertilizantes):
        self.producao_estimada = producao
        self.uso_agua = agua
        self.uso_fertilizantes = fertilizantes

    def calcular_indice_sustentabilidade(self):
        """
        Calcula o equilíbrio entre produção e impacto ambiental.
        Pontuação de 0 a 100 (Quanto maior, mais sustentável).
        """
        # Penalidades baseadas em excessos
        ponto_agua = max(0, 100 - (self.uso_agua * 0.1))
        ponto_fertilizante = max(0, 100 - (self.uso_fertilizantes * 0.5))
        
        # Bônus por alta produtividade por hectare
        produtividade_ha = self.producao_estimada / self.area
        ponto_produtividade = min(100, produtividade_ha * 10)
        
        # Média ponderada: equilíbrio é a chave!
        indice_final = (ponto_agua * 0.35) + (ponto_fertilizante * 0.35) + (ponto_produtividade * 0.30)
        return indice_final

    def gerar_relatorio(self):
        indice = self.calcular_indice_sustentabilidade()
        
        print("\n" + "="*50)
        print(f"🌱 PAINEL DE SUSTENTABILIDADE: {self.nome.upper()} 🌱")
        print("Tema: Agro forte, futuro sustentável")
        print("="*50)
        print(f"📊 Área Cultivada: {self.area} hectares")
        print(f"🚜 Produção Estimada: {self.producao_estimada} toneladas")
        print(f"💧 Consumo de Água: {self.uso_agua} L/kg")
        print(f"🧪 Fertilizantes: {self.uso_fertilizantes} kg/hectare")
        print("-"*50)
        print(f"✨ ÍNDICE DE EQUILÍBRIO AMBIENTAL: {indice:.2f}/100")
        print("-"*50)
        
        # Diagnóstico e Recomendações
        if indice >= 75:
            print("🚀 Diagnóstico: Agro Forte e Sustentável! Excelente equilíbrio.")
            print("💡 Dica: Continue utilizando técnicas de plantio direto e rotação de culturas.")
        elif 50 <= indice < 75:
            print("⚠️ Diagnóstico: Produção estável, mas o impacto ambiental pode ser reduzido.")
            print("💡 Dica: Considere adotar irrigação gota a gota para otimizar o uso da água.")
        else:
            print("🚨 Diagnóstico: Alerta Vermelho! Alto impacto ambiental detectado.")
            print("💡 Dica: Reduza o uso de insumos químicos e invista em biofertilizantes urgentemente.")
        print("="*50 + "\n")

# --- SIMULAÇÃO DO SISTEMA ---
if __name__ == "__main__":
    print("Iniciando Sistema de Monitoramento AgroSustentável...")
    time.sleep(1)
    
    # Criando a fazenda modelo
    minha_fazenda = FazendaSustentavel(nome="Fazenda Futuro Verde", area_hectares=500)
    
    # Simulando dados coletados por sensores (Produção, Água L/kg, Fertilizante kg/ha)
    # Cenário: Alta produção com práticas controladas
    minha_fazenda.monitorar_safra(producao=4500, agua=150, fertilizantes=60)
    
    # Exibindo os resultados no terminal
    minha_fazenda.gerar_rel
