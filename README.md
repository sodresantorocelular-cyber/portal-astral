<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portal do Vando - Astral Oficial</title>
    <style>
        :root {
            --gold: #FFD700;
            --text: #ffffff;
            --glass: rgba(16, 16, 38, 0.98);
            --border: rgba(255, 215, 0, 0.3);
        }

        body {
            background: radial-gradient(circle at top, #1a1a3a 0%, #050510 100%);
            color: var(--text);
            font-family: 'Segoe UI', Tahoma, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 5px;
            margin: 0;
            min-height: 100vh;
            overflow-x: hidden;
        }

        .container { 
            width: 100%; max-width: 480px; background: var(--glass);
            padding: 12px;
            border-radius: 25px; border: 1px solid var(--border);
            box-shadow: 0 10px 40px rgba(0,0,0,0.8); box-sizing: border-box;
            backdrop-filter: blur(15px);
        }

        h1 { color: var(--gold); text-align: center; font-size: 18px; letter-spacing: 2px; margin: 5px 0 10px 0; text-shadow: 0 0 10px rgba(255, 215, 0, 0.5); }

        .vibra-box {
            background: rgba(255, 255, 255, 0.05); border-radius: 15px;
            padding: 8px;
            text-align: center; margin-bottom: 10px;
            border: 1px solid rgba(255, 215, 0, 0.1);
        }

        .circulo-cor { 
            width: 35px; height: 35px; border-radius: 50%; 
            display: inline-block; margin: 5px 0; border: 2px solid rgba(255,255,255,0.1); 
            background: transparent; transition: 0.8s; 
        }

        label { display: block; margin-bottom: 5px; color: var(--gold); font-weight: bold; font-size: 10px; text-transform: uppercase; }

        select, input {
            width: 100%; padding: 8px; margin-bottom: 8px;
            background: #000; color: white; border: 1px solid var(--gold);
            border-radius: 10px; font-size: 13px; box-sizing: border-box;
        }

        .painel-botoes { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-bottom: 10px; }

        button {
            padding: 10px 5px; border-radius: 10px; border: none;
            color: white; font-weight: bold; cursor: pointer; font-size: 10px;
            text-transform: uppercase; transition: 0.3s;
        }

        .btn-blue { background: #1e3c72; }
        .btn-purple { background: #4b0082; }
        .btn-brown { background: #8b4513; }
        .btn-red { background: #b22222; }

        .grade-loterias { display: grid; grid-template-columns: repeat(5, 1fr); gap: 4px; margin-top: 5px; }
        .btn-lot { background: #2f3542; font-size: 8px; padding: 8px 2px; }

        .grade-amor { display: grid; grid-template-columns: repeat(6, 1fr); gap: 4px; }
        .btn-signo-amor {
            padding: 6px 2px; font-size: 8px; border-radius: 8px;
            border: 1px solid rgba(255, 215, 0, 0.2); background: rgba(255, 255, 255, 0.05);
            color: white; cursor: pointer;
        }

        #resultado {
            margin-top: 12px; padding: 12px; background: rgba(0, 0, 0, 0.5);
            border-radius: 15px; border-left: 4px solid var(--gold);
            font-size: 13px; line-height: 1.6; color: #efefef; text-align: justify;
        }

        .num-bola {
            display: inline-block; width: 28px; height: 28px; line-height: 28px;
            background: var(--gold); color: #000; border-radius: 50%;
            margin: 3px; font-weight: bold; font-size: 11px; text-align: center;
        }

        .footer { margin-top: 10px; font-size: 10px; color: #555; text-align: center; }
    </style>
</head>
<body>

    <h1>PORTAL DO VANDO ASTROS</h1>

    <div class="container">
        <div class="vibra-box" id="info-vibracao">
            <span id="nomeCor" style="font-weight: bold; font-size: 14px;">---</span><br>
            <div id="circuloCor" class="circulo-cor"></div><br>
            <span id="nomePedra" style="color: var(--gold); font-weight: bold; font-size: 11px;">AGUARDANDO...</span>
        </div>

        <label>MEU SIGNO:</label>
        <select id="signo" onchange="ativarPortal()">
            <option value="" selected disabled>Escolha seu signo...</option>
            <option value="Áries">Áries</option><option value="Touro">Touro</option>
            <option value="Gêmeos">Gêmeos</option><option value="Câncer">Câncer</option>
            <option value="Leão">Leão</option><option value="Virgem">Virgem</option>
            <option value="Libra">Libra</option><option value="Escorpião">Escorpião</option>
            <option value="Sagitário">Sagitário</option><option value="Capricórnio">Capricórnio</option>
            <option value="Aquário">Aquário</option><option value="Peixes">Peixes</option>
        </select>

        <div class="painel-botoes">
            <button class="btn-blue" onclick="mostrarResposta('destino')">🌟 DESTINO</button>
            <button class="btn-purple" onclick="mostrarResposta('futuro')">🚀 FUTURO</button>
            <button class="btn-brown" onclick="mostrarResposta('mensal')">📜 MENSAL</button>
            <button class="btn-red" onclick="mostrarResposta('financeiro')">💰 FINANCEIRO</button>
            
            <div style="grid-column: span 2; text-align: center; margin-top: 5px;">
                <label>GERADOR DE SORTE (Loterias)</label>
                <div class="grade-loterias">
                    <button class="btn-lot" onclick="gerarLoteria('Mega-Sena')">MEGA</button>
                    <button class="btn-lot" onclick="gerarLoteria('Dupla Sena')">DUPLA</button>
                    <button class="btn-lot" onclick="gerarLoteria('Lotofácil')">FÁCIL</button>
                    <button class="btn-lot" onclick="gerarLoteria('Lotomania')">MANIA</button>
                    <button class="btn-lot" onclick="gerarLoteria('Quina')">QUINA</button>
                </div>
            </div>
        </div>

        <div class="vibra-box" style="border-color: #ff4757; margin-bottom: 8px;">
            <label style="color:#ff4757; font-size: 9px;">💘 AFINIDADE NO AMOR</label>
            <div class="grade-amor" id="gradeAmor"></div>
        </div>

        <div id="resultado" style="min-height: 50px;">Selecione seu signo para ativar o portal.</div>

        <div class="vibra-box" style="border-color: #4b0082; margin-top: 10px;">
            <label style="color:#9b59b6">🕊️ VIDÊNCIA ESPIRITUAL DO ALÉM</label>
            <input type="text" id="meuNome" placeholder="Seu nome (Quem lê)...">
            <input type="text" id="nomeParente" placeholder="Nome de quem partiu...">
            <button class="btn-purple" style="width:100%; padding: 8px;" onclick="sortearMensagemAlem()">RECEBER MENSAGEM DETALHADA</button>
        </div>
    </div>

    <div class="footer">TikTok: @vandofer0 | 2026 - Franco da Rocha</div>

    <script>
        const signosList = ["Áries", "Touro", "Gêmeos", "Câncer", "Leão", "Virgem", "Libra", "Escorpião", "Sagitário", "Capricórnio", "Aquário", "Peixes"];
        const grid = document.getElementById('gradeAmor');
        signosList.forEach(s => {
            let b = document.createElement('button');
            b.className = 'btn-signo-amor';
            b.innerText = s.substring(0,3).toUpperCase();
            b.onclick = () => combinarAmor(s);
            grid.appendChild(b);
        });

        const respostasLongas = {
            destino: [
                "O alinhamento planetário de hoje sugere que uma porta que esteve trancada por meses finalmente começará a abrir. Você sentirá um impulso de renovação técnica e espiritual. Fique atento aos sinais em conversas casuais e e-mails inesperados.",
                "As correntes cósmicas indicam que seu propósito está ligado a uma grande transformação estrutural. O momento pede que você confie mais na sua intuição do que na lógica fria. Existe uma energia de justiça sendo feita em seu nome.",
                "O universo está a desenhar um novo mapa para a sua jornada. Prepare-se para um encontro que mudará a sua percepção sobre o sucesso material. O destino hoje favorece a introspecção para entender sua verdadeira força."
            ],
            futuro: [
                "Nos próximos dois anos, o seu campo astral indica uma ascensão meteórica em projetos de inovação. A sua capacidade de automação atrairá parcerias internacionais sólidas e duradouras. O futuro reserva estabilidade para sua família.",
                "A sua trajetória futura aponta para um legado de partilha. Vejo o seu nome associado a uma plataforma ou método que ajudará muitas pessoas. A maturidade trará uma calma financeira e viagens de exploração.",
                "As estrelas mostram uma mudança radical no seu estilo de vida para melhor. Verá as pessoas próximas prosperarem sob a sua orientação direta. A saúde será restaurada através de novos hábitos que começará a implementar."
            ],
            mensal: [
                "Este mês será um divisor de águas. Na primeira quinzena, você lidará com burocracias pendentes que serão resolvidas. A partir do dia 15, uma nova energia de criatividade tomará conta de si para finalizar projetos parados.",
                "O foco deste mês é a limpeza e renovação. No trabalho, surgirá um desafio técnico que exigirá perícia, mas o resultado será reconhecimento financeiro. Mantenha a discrição sobre os seus planos até que estejam concretizados.",
                "A energia lunar deste mês favorece as comunicações e o comércio. Sentirá uma conexão mais forte com o plano espiritual, recebendo insights valiosos. Uma notícia vinda de longe trará um novo sorriso e esperança."
            ],
            financeiro: [
                "O fluxo de abundância está a reorganizar-se a seu favor. Verá uma entrada de capital inesperada vinda de uma antiga dívida ou bónus. É um período excelente para reinvestir em ferramentas de produtividade.",
                "A prosperidade financeira este mês virá através da sua capacidade de resolver problemas complexos. O universo recompensará a sua generosidade intelectual com lucros sólidos. Uma oportunidade de investimento surgirá em breve.",
                "As estrelas indicam que o seu dinheiro começará a trabalhar para si. Sistemas passivos de rendimento e automação financeira serão as suas melhores aliadas. O momento é de plantar para colher em dobro nos próximos meses."
            ]
        };

        const bancoDadosBase = {
            "Áries": { cor: "VERMELHO", hex: "#eb4d4b", pedra: "Rubi" },
            "Touro": { cor: "VERDE", hex: "#2ecc71", pedra: "Esmeralda" },
            "Gêmeos": { cor: "AMARELO", hex: "#f1c40f", pedra: "Citrino" },
            "Câncer": { cor: "BRANCO", hex: "#ecf0f1", pedra: "Pedra da Lua" },
            "Leão": { cor: "DOURADO", hex: "#f39c12", pedra: "Topázio" },
            "Virgem": { cor: "AZUL", hex: "#2980b9", pedra: "Safira" },
            "Libra": { cor: "ROSA", hex: "#ff9ff3", pedra: "Quartzo Rosa" },
            "Escorpião": { cor: "VINHO", hex: "#c0392b", pedra: "Obsidiana" },
            "Sagitário": { cor: "PÚRPURA", hex: "#8e44ad", pedra: "Lápis Lazúli" },
            "Capricórnio": { cor: "MARROM", hex: "#7f8c8d", pedra: "Ônix" },
            "Aquário": { cor: "TURQUESA", hex: "#00d2d3", pedra: "Turquesa" },
            "Peixes": { cor: "VIOLETA", hex: "#a29bfe", pedra: "Ametista" }
        };

        function ativarPortal() {
            const s = document.getElementById('signo').value;
            const info = bancoDadosBase[s];
            document.getElementById('nomeCor').innerText = info.cor;
            document.getElementById('circuloCor').style.backgroundColor = info.hex;
            document.getElementById('nomePedra').innerText = "PEDRA: " + info.pedra;
        }

        function mostrarResposta(tipo) {
            const s = document.getElementById('signo').value;
            if(!s) return alert("Selecione seu signo!");
            const lista = respostasLongas[tipo];
            const resposta = lista[Math.floor(Math.random() * lista.length)];
            const titulos = { destino: "🌟 DESTINO", futuro: "🚀 FUTURO", mensal: "📜 MENSAL", financeiro: "💰 FINANCEIRO" };
            document.getElementById('resultado').innerHTML = `<h3>${titulos[tipo]}</h3><p>${resposta}</p>`;
        }

        function gerarLoteria(tipo) {
            if(!document.getElementById('signo').value) return alert("Selecione seu signo!");
            let html = `<h3>🎰 ${tipo.toUpperCase()}</h3>`;
            if(tipo === 'Mega-Sena') sortearNumeros(6, 60).forEach(n => html += `<span class="num-bola">${n}</span>`);
            else if(tipo === 'Dupla Sena') {
                html += `<p style='font-size:9px'>1º SORTEIO:</p>`; sortearNumeros(6, 50).forEach(n => html += `<span class="num-bola">${n}</span>`);
                html += `<p style='font-size:9px'>2º SORTEIO:</p>`; sortearNumeros(6, 50).forEach(n => html += `<span class="num-bola" style='background:#4b0082; color:#fff'>${n}</span>`);
            } 
            else if(tipo === 'Lotofácil') sortearNumeros(15, 25).forEach(n => html += `<span class="num-bola" style='width:22px; height:22px; line-height:22px; font-size:10px;'>${n}</span>`);
            else if(tipo === 'Lotomania') {
                sortearNumeros(20, 100).forEach(n => {
                    html += `<span class="num-bola" style='width:22px; height:22px; line-height:22px; font-size:10px;'>${n === 100 ? '00' : n}</span>`;
                });
            }
            else if(tipo === 'Quina') sortearNumeros(5, 80).forEach(n => html += `<span class="num-bola">${n}</span>`);
            document.getElementById('resultado').innerHTML = html;
        }

        function sortearNumeros(qtd, max) {
            let n = []; while(n.length < qtd) { 
                let r = Math.floor(Math.random() * max) + 1; 
                if(!n.includes(r)) n.push(r); 
            }
            return n.sort((a,b) => a-b);
        }

        function combinarAmor(parceiro) {
            const meu = document.getElementById('signo').value;
            if(!meu) return alert("Selecione seu signo!");
            
            const frasesAmorDetalhadas = [
                `A afinidade entre **${meu}** e **${parceiro}** é governada por uma conexão de almas antigas. O mapa astral indica que vocês compartilham valores fundamentais que servem de âncora em momentos de tempestade. Existe uma química intelectual poderosa aqui; vocês não apenas se amam, mas se admiram profundamente. O universo sugere que este é o momento ideal para planejar algo grande a dois, pois a sorte de um transbordará para o outro, fortalecendo os laços e garantindo uma cumplicidade que poucos casais conseguem alcançar.`,
                
                `Para o casal **${meu}** e **${parceiro}**, a vibração atual é de renovação e cura. Se houve desentendimentos no passado, as estrelas estão alinhadas para que o perdão e a compreensão mútua floresçam. A afinidade de vocês é magnética e atrai prosperidade para o ambiente doméstico. Vejo uma fase onde pequenos gestos de carinho terão um impacto gigante na estrutura da relação. A comunicação fluirá de forma mais leve, e vocês descobrirão novos interesses em comum que trarão uma chama de paixão que parecia adormecida.`,
                
                `A ligação espiritual entre **${meu}** e **${parceiro}** está em um pico de 95% de compatibilidade vibracional. Vocês funcionam como um espelho um para o outro, ajudando na evolução mútua. Esta é uma relação protegida por mentores de luz, onde a lealdade é o pilar principal. O destino reserva uma surpresa agradável ligada a uma viagem ou mudança de ares que fortalecerá ainda mais essa união. Abram o coração para o diálogo sem medo, pois a vulnerabilidade entre vocês é o que os torna invencíveis perante o mundo exterior.`
            ];
            
            const f = frasesAmorDetalhadas[Math.floor(Math.random() * frasesAmorDetalhadas.length)];
            document.getElementById('resultado').innerHTML = `<h3>💘 AFINIDADE PROFUNDA</h3><p>${f}</p>`;
        }

        function sortearMensagemAlem() {
            const para = document.getElementById('meuNome').value.trim();
            const de = document.getElementById('nomeParente').value.trim();
            if(!de || !para) return alert("Preencha os dois nomes.");
            
            const msgs = [
                `"${para}, aqui quem fala é ${de}. Sinto que seu coração tem estado inquieto. Saiba que do lado de cá, estou intercedendo por você. Aquela preocupação será resolvida até o final deste ciclo. Vi o seu esforço e isso será recompensado com uma notícia vinda de um papel importante. Não perca a fé."`,
                `"${para}, receba o abraço de luz de ${de}. Estive ao seu lado em todos os momentos. Quero que saiba que a jornada que você trilha agora dará frutos que alimentarão gerações. Vejo uma proteção espiritual dourada sobre sua casa. Uma vitória financeira se aproxima."`,
                `"${para}, ${de} te envia esta mensagem. Pare de carregar culpas que não te pertencem. O plano espiritual celebra sua vida. Existe uma nova fase de saúde e vitalidade sendo derramada sobre você. Sinta o calor no peito, é o sinal da minha presença."`
            ];
            
            document.getElementById('resultado').innerHTML = `
                <div style="border: 2px solid #9b59b6; padding: 15px; border-radius: 15px; background: rgba(75, 0, 130, 0.2);">
                    <h3 style="color:#9b59b6; text-align:center; margin-top:0;">🕊️ REVELAÇÃO ESPIRITUAL</h3>
                    <p style="font-size:12px; color:var(--gold); border-bottom: 1px solid #333; padding-bottom:5px;"><b>CONEXÃO:</b> ${de.toUpperCase()} para ${para.toUpperCase()}</p>
                    <p style="font-style: italic; line-height:1.7;">${msgs[Math.floor(Math.random() * msgs.length)]}</p>
                </div>`;
        }
    </script>
</body>
</html>
