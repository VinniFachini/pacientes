<template>
  <div class="container mx-auto p-6">
    <h1 class="text-4xl font-bold text-indigo-600 mb-4">Criar Novo Histórico</h1>
    <form @submit.prevent="submitForm" class="space-y-4">
      <!-- Identificação -->
      <h2 class="text-2xl font-semibold text-gray-700 mb-2">Identificação</h2>
      <div>
        <label for="nome" class="block text-sm font-semibold text-gray-700">Nome</label>
        <input
          v-model="historico.identificacao.nome"
          type="text"
          id="nome"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="idade" class="block text-sm font-semibold text-gray-700">Idade</label>
        <input
          v-model="historico.identificacao.idade"
          type="number"
          id="idade"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="nascimento" class="block text-sm font-semibold text-gray-700"
          >Data de Nascimento</label
        >
        <input
          v-model="historico.identificacao.nascimento"
          type="date"
          id="nascimento"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="leito" class="block text-sm font-semibold text-gray-700">Leito</label>
        <input
          v-model="historico.identificacao.leito"
          type="number"
          id="leito"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="estado_civil" class="block text-sm font-semibold text-gray-700"
          >Estado Civil</label
        >
        <input
          v-model="historico.identificacao.estado_civil"
          type="text"
          id="estado_civil"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="filhos" class="block text-sm font-semibold text-gray-700"
          >Filhos (idades)</label
        >
        <input
          v-model="historico.identificacao.filhos"
          type="text"
          id="filhos"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
          placeholder="Ex: 12, 15"
        />
      </div>
      <div>
        <label for="genero" class="block text-sm font-semibold text-gray-700"
          >Gênero</label
        >
        <input
          v-model="historico.identificacao.genero"
          type="text"
          id="genero"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="escolaridade" class="block text-sm font-semibold text-gray-700"
          >Escolaridade</label
        >
        <input
          v-model="historico.identificacao.escolaridade"
          type="text"
          id="escolaridade"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="etnia" class="block text-sm font-semibold text-gray-700">Etnia</label>
        <input
          v-model="historico.identificacao.etnia"
          type="text"
          id="etnia"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="ocupacao" class="block text-sm font-semibold text-gray-700"
          >Ocupação</label
        >
        <input
          v-model="historico.identificacao.ocupacao"
          type="text"
          id="ocupacao"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="naturalidade" class="block text-sm font-semibold text-gray-700"
          >Naturalidade</label
        >
        <input
          v-model="historico.identificacao.naturalidade"
          type="text"
          id="naturalidade"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="procedencia" class="block text-sm font-semibold text-gray-700"
          >Procedência</label
        >
        <input
          v-model="historico.identificacao.procedencia"
          type="text"
          id="procedencia"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="religiao" class="block text-sm font-semibold text-gray-700"
          >Religião</label
        >
        <input
          v-model="historico.identificacao.religiao"
          type="text"
          id="religiao"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="cuidador" class="block text-sm font-semibold text-gray-700"
          >Cuidador</label
        >
        <select
          v-model="historico.identificacao.cuidador"
          id="cuidador"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        >
          <option value="Sim">Sim</option>
          <option value="Não">Não</option>
        </select>
      </div>
      <div>
        <label for="grupo_sanguineo" class="block text-sm font-semibold text-gray-700"
          >Grupo Sanguíneo</label
        >
        <input
          v-model="historico.identificacao.grupo_sanguineo"
          type="text"
          id="grupo_sanguineo"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="fator_rh" class="block text-sm font-semibold text-gray-700"
          >Fator RH</label
        >
        <input
          v-model="historico.identificacao.fator_rh"
          type="text"
          id="fator_rh"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>

      <h2 class="text-2xl font-semibold text-gray-800">
        Informações sobre Doença e Tratamento
      </h2>
      <div>
        <label for="motivo_internacao" class="block text-sm font-semibold text-gray-700"
          >Motivo da Internação</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.motivo_internacao"
          type="text"
          id="motivo_internacao"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="diagnostico_medico" class="block text-sm font-semibold text-gray-700"
          >Diagnóstico Médico</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.diagnostico_medico"
          type="text"
          id="diagnostico_medico"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="doencas_cronicas" class="block text-sm font-semibold text-gray-700"
          >Doenças Crônicas</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.doencas_cronicas"
          type="text"
          id="doencas_cronicas"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="fatores_risco" class="block text-sm font-semibold text-gray-700"
          >Fatores de Risco</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.fatores_risco"
          type="text"
          id="fatores_risco"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="cirurgias" class="block text-sm font-semibold text-gray-700"
          >Cirurgias</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.cirurgias"
          type="text"
          id="cirurgias"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="outros_tratamentos" class="block text-sm font-semibold text-gray-700"
          >Outros Tratamentos</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.outros_tratamentos"
          type="text"
          id="outros_tratamentos"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label
          for="alergias_medicamentos"
          class="block text-sm font-semibold text-gray-700"
          >Alergia a Medicamentos</label
        >
        <select
          v-model="historico.informacoes_doenca_tratamento.alergias_medicamentos"
          id="alergias_medicamentos"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        >
          <option value="true">Sim</option>
          <option value="false">Não</option>
        </select>
      </div>
      <div>
        <label for="especificar" class="block text-sm font-semibold text-gray-700"
          >Especificar</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.especificar"
          type="text"
          id="especificar"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label
          for="tratamentos_anteriores"
          class="block text-sm font-semibold text-gray-700"
          >Tratamentos Anteriores</label
        >
        <input
          v-model="historico.informacoes_doenca_tratamento.tratamentos_anteriores"
          type="text"
          id="tratamentos_anteriores"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>

      <!-- Socioeconômicos Culturais -->
      <h2 class="text-2xl font-semibold text-gray-700 mt-4 mb-2">
        Socioeconômicos Culturais
      </h2>
      <div>
        <label for="moradia" class="block text-sm font-semibold text-gray-700"
          >Moradia</label
        >
        <input
          v-model="historico.socio_economicos_culturais.moradia"
          type="text"
          id="moradia"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="animais_domesticos" class="block text-sm font-semibold text-gray-700"
          >Animais Domésticos</label
        >
        <input
          v-model="historico.socio_economicos_culturais.animais_domesticos"
          type="text"
          id="animais_domesticos"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>

      <!-- Higiene -->
      <h2 class="text-2xl font-semibold text-gray-700 mt-4 mb-2">Higiene</h2>
      <div>
        <label for="habito_tomar_banho" class="block text-sm font-semibold text-gray-700"
          >Hábito de Tomar Banho</label
        >
        <input
          v-model="historico.higiene.habito_tomar_banho"
          type="text"
          id="habito_tomar_banho"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label
          for="atividade_fisica_trabalho"
          class="block text-sm font-semibold text-gray-700"
          >Atividade Física no Trabalho</label
        >
        <input
          v-model="historico.higiene.atividade_fisica_trabalho"
          type="text"
          id="atividade_fisica_trabalho"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="fumo" class="block text-sm font-semibold text-gray-700">Fumo</label>
        <input
          v-model="historico.higiene.fumo"
          type="text"
          id="fumo"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="alcool" class="block text-sm font-semibold text-gray-700"
          >Álcool</label
        >
        <input
          v-model="historico.higiene.alcool"
          type="text"
          id="alcool"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="sono_repouso" class="block text-sm font-semibold text-gray-700"
          >Sono Repouso</label
        >
        <input
          v-model="historico.higiene.sono_repouso"
          type="text"
          id="sono_repouso"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="exercicios_fisicos" class="block text-sm font-semibold text-gray-700"
          >Exercícios Físicos</label
        >
        <input
          v-model="historico.higiene.exercicios_fisicos"
          type="text"
          id="exercicios_fisicos"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label for="eliminacao_urinaria" class="block text-sm font-semibold text-gray-700"
          >Eliminação Urinaria</label
        >
        <input
          v-model="historico.higiene.eliminacao_urinaria"
          type="text"
          id="eliminacao_urinaria"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <div>
        <label
          for="eliminacoes_intestinais"
          class="block text-sm font-semibold text-gray-700"
          >Eliminação Intestinal</label
        >
        <input
          v-model="historico.higiene.eliminacoes_intestinais"
          type="text"
          id="eliminacoes_intestinais"
          class="mt-1 block w-full border border-gray-300 rounded-md p-2"
        />
      </div>
      <!-- Outros campos de Higiene -->

      <button
        type="submit"
        class="mt-4 bg-indigo-600 text-white font-semibold py-2 px-4 rounded hover:bg-indigo-700 transition-colors"
      >
        Criar Histórico
      </button>
    </form>
    <section class="info">
      <h1>Exame Físico de Enfermagem</h1>
      <p>
        O exame físico é conceituado como processo de exame do corpo de um paciente, com o
        objetivo de determinar presença ou ausência de problemas físicos. O exame físico é
        compreendido em 4 fases seguidas que devem ser: Inspeção, palpação, percussão e
        ausculta.
      </p>
      <ul class="list">
        <h3>Posições</h3>
        <li>Decúbito dorsal</li>
        <li>Decúbito ventral</li>
        <li>Decúbito latertal (direito e esquerdo)</li>
        <li>posição sentada</li>
        <li>posição ortostática</li>
      </ul>
      <article>
        <h3>Instrumentos necessários para o exame físico em hemodinâmica</h3>
        <p>
          Inspeção: Diz respeito a uma observação onde é realizada uma comparação entre os
          lados do corpo. É realizada uma Inspeção de cada área quanto ao seu tamanho,
          formato, coloração, simetria, posição e deformidades.
        </p>
        <p>
          Palpação: o examinador utiliza as mãos para tentar enxergar aquilo que não é
          possível aos seus olhos. Ao aplicar uma pressão sobre uma determinada área
          corporal o examinador tenta identificar nódulos ou massas. Verificando sinais
          físicos específicos como resistência, elasticidade, rugosidade, textura e
          mobilidade.
        </p>
        <p>
          Percussão: Consiste na produção de vibração e consequentes ondas sonoras através
          do batimento da superfície corporal diretamente ou indiretamente com um dos seus
          dedos. devido as densidades dos diferentes órgãos do corpo humano cada um deles
          produz características identificadas à percussão. São estes: timpânico, maciço e
          sub-maciço. Estômago: Timpanismo, Fígado: Submacicez
        </p>
        <p>Ausculta: Consiste na ausculta com a utilização de um estetoscópio.</p>
        <h4>Tipos de som:</h4>
        <ul class="list">
          <li>
            Som timpânico: Área de ar que contenha recoberta por uma membrana flexível -
            Caixa Vazia intestino, espaço de Traube (fundo do estômago) (elasticidade)
            Tambor-caixa vazia.
          </li>
          <li>
            Som Maciço: Regiões desprovidas de ar - coxa, coração, fígado e baço.
            (acompanha-se de dureza e resistência) - Parede, bloco de madeira.
          </li>
          <li>
            Som submaciço: Variação do som maciço -presença de ar lhe dá uma
            característica peculiar - livro grosso, tórax pouco ar
          </li>
          <li>Som claro pulmonar: som que se obtém quando se golpeia um tórax normal.</li>
        </ul>
        <p>
          Os sons obtidos podem ser classificados quanto a intensidade, tonalidade e
          timbre - qualidades fundamentais do som - livro grosso.
        </p>
      </article>

      <article>
        <h3>Fases do Exame Físico</h3>
        <p>
          Observação da aparência geral do cliente; Sinais vitais (Temperatura, Pulso,
          Respiração e Pressão Arterial). É importante verificar os pulsos: carotídeo,
          braquial, radial, femoral, tibial posterior, poplíteo e pedioso.
        </p>
        <ol class="list">
          <li>
            <h4>Pele</h4>
            <p>
              Cianose Central - Decorrente da inadequada oxigenação do sangue arterial nos
              pulmões. Correlaciona-se diretamente com uma hipoxemia e hipóxia celular
              provocando uma coloração azulada que é melhor observada nos lábios, língua e
              mucosa oral.
            </p>
            <p>
              Cianose periférica - coloração azulada nas extremidades periféricas (Ponta
              dos Dedos).
            </p>
            <p>
              Palidez - Diminuição da cor devido a uma quantidade reduzida de
              oxiemoglobina, ou visibilidade reduzida da mesma resultante da diminuição do
              fluxo sanguíneo, geralmente provocada por anemia e choque respectivamente.
              Melhor observada na face, conjuntivas, leitos ungueais e palma das mãos.
            </p>
            <p>
              Icterícia - Aumento de depósito de bilirrubina nos tecidos - coloração
              amarelo alaranjada.
            </p>
            <p>
              Eritema - Aumento da visibilidade da oxiemoglobina devido a dilatação ou
              fluxo sanguíneo aumentado. Provocado por febre, trauma direto, rubor e
              ingestão de álcool, observado rosto e em locais onde há maior pressão de
              estrutura óssea contra uma superfície rígida.
            </p>
            <p>
              Petéquia - Manchas hemorrágicas puntiformes. Equimose - manchas
              hemorrágicas. Hematoma - manchas hemorrágicas em grande volume no local.
            </p>
            <p>
              Edema - Extravasamento de líquidos para o espaço intersticial. Trauma direto
              e comprometimento do retorno venoso são causas comuns de edema. É importante
              avaliar o grau de fim de um edema estabelecer parâmetros de comparação, para
              isso é utilizado o sinal de cacifo. É realizada uma pressão com o polegar
              sobre a área avaliada por aproximadamente 5 segundos. A profundidade do
              cacifo é registrada da seguinte forma, utilizando uma escala de 1 a + 4.
            </p>
            <p>
              Turgor - Consiste na avaliação da elasticidade da pele. Para examinar o
              turgor cutâneo, uma prega da pele sob uma parte posterior do antebraço ou
              área do externo é presa com uma ponta dos dedos e liberada. O enfermeiro uma
              observa facilidade com que a pele e movimenta e a velocidade com que retorna
              à sua posição normal. O fracasso da Pele em reassumir o seu contorno ou
              formato desidratação indica normal. Descamação - aparência de flocos tipo
              caspa. Escamação - aparência tipo escama de peixe.
            </p>
          </li>
          <li>
            <h4>Cabeça</h4>
            <p>Crânio Macrocefalia - crânio anormalmente grande</p>
            <p>Microcefalia - crânio anormalmente pequeno</p>
            <p>
              Couro cabeludo: Inflamações (foliculites, abscessos), Pediculose: lêndeas e
              piolhos, Sujidade: seborreia.
            </p>
          </li>
          <li>
            <h4>Sobrancelha</h4>
            <p>Verificar a sua simetria</p>
          </li>
          <li>
            <h4>Olhos</h4>
            <p>
              Pálpebras xantelasma - lesões cutâneas da região palpebral provocadas pelo
              depósito de lipídeos na pele.
            </p>
            <p>
              Blefarite ulcerativa – inflamação das pálpebras que pode apresentar úlceras
              superficiais nas bordas das pálpebras.
            </p>
            <p>Crostas hordéolos - Infecção estafilocócica das glândulas palpebrais.</p>
            <p>
              Exoftalmia - Protrusão anormal de um ou de ambos os olhos fechamento das
              pálpebras (Pálpebra caída).
            </p>
            <p>Conjuntiva palidez (anemias)</p>
            <p>Conjuntivite, esclerótica icterícia (Amarelão)</p>
            <p>Pterígio (tecido carnoso que cresce sobre a córnea)</p>
            <p>Pupila midríase - Diâmetro aumentado</p>
            <p>Miose - Diminuído diâmetro</p>
          </li>
          <li>
            <h4>Boca-Lábios</h4>
            <p>Cianose queilose - Das rachaduras comissuras labiais.</p>
            <p>Queilite - Rachadura na presença de pus.</p>
            <p>
              Língua saburrosa - Camada esbranquiçada que surge na ausência de mastigação
              por 24 horas.
            </p>
            <p>Glossite - Vermelho vivo com uma sensibilidade alimentos quentes.</p>
            <p>Macroglossia - Aumento da língua global.</p>
          </li>
          <li>
            <h4>Pescoço</h4>
            <p>
              Observar-se a presença de nódulos massas, turgência de Jugulares e desvio de
              traqueia. Enfisematoso, do barril, em tonel, globoso etc.
            </p>
            <p>Gânglio occipital: Abaixo da proeminência occipital.</p>
            <p>Gânglio retroauricular: Abaixo do processo mastoide.</p>
            <p>Gânglio pré-auricular: Frente ao ouvido.</p>
            <p>Gânglio retro faringianos: Abaixo do ângulo da mandíbula.</p>
            <p>
              Gânglio submandibular: Abaixo da linha da mandíbula o média, entre mento E o
              Gânglio da mandíbula.
            </p>
            <p>Gânglio sub-mentoniano: Abaixo do processo mentual da mandíbula.</p>
            <h5>Palpação da tireoide.</h5>
            O examinador posiciona-se atrás ou a frente do cliente, que flexiona o pescoço
            para frente e lateralmente na direção do lado que está sendo examinado, ao
            pedir que o cliente degluta o examinador sente com os dedos posicionados de
            cada lado da traqueia. Estase jugular
          </li>
          <li>
            <h4>Membros Superiores (D e E)</h4>
            <p>
              Verificar se a pele está integra, alguma Anormalidade, alguma fratura,
              verificar perfusão Tissular está eficaz ou não, etc...
            </p>
          </li>
          <li>
            <h4>Tórax</h4>
            <p>Verificar as mamas (simetria).</p>
            <p>
              Mitral em Foco: na Sede do Ictus Cordis (5 ° espaço intercostal, Esquerdo
              Linha hemiclavicular).
            </p>
            <p>Foco tricúspide: Na base do apêndice xifoide.</p>
            <p>Pulmonar em Foco: 2 ° Espaço intercostal Direito, linha paresternal.</p>
            <p>Aórtico em Foco: 2 ° Espaço intercostal esquerdo, linha paresternal.</p>
            <p>
              Foco aórtico acessório (ponto de ERB): 3 ° espaço intercostal esquerdo,
              linha parestenal.
            </p>
            <p>Bulhas cardíacas:</p>
            <p>
              1 ° bulha cardíaca (B1): corresponde simultâneo ao fechamento das valvas
              tricúspide e mitral. É melhor ouvida sem foco e sem foco mitral tricúspide,
              ela mostra-se na sístole. TUM.
            </p>
            <p>
              2° bulha cardíaca (B2): corresponde simultâneo ao fechamento das valvas
              pulmonar e aórtica. É melhor ouvida sem foco pulmonar e foco aórtico. TA
            </p>
            <strong
              >Obs.: A abertura das valvas só pode ser ouvida se estas estiverem lesadas.
              Posição do paciente e examinador: Descoberto, decúbito dorsal, cabeça
              apoiada em um travesseiro pequeno, examinador a direita em pé ou
              sentado</strong
            >
          </li>
          <li>
            <h4>Pulmão</h4>
            <p>Respiração torácica- respiração comum nas mulheres</p>
            <p>Respiração abdominal e respiração tóraco-abdominal - Comum nos homens</p>
            <p>
              Murmúrios vesiculares: São sons respiratórios normais, produzidos
              turbulência da entrada do ar e pelos alvéolos bronquíolos. São audíveis em
              todos os campos pulmonares.
            </p>
            <p>
              Ruídos adventícios: São sons respiratórios anormais que se superpõem aos
              sons respiratórios normais. Podem ser:
            </p>
            <p>
              Crepitantes: Audíveis quando há abertura súbita das vias aéreas pequenas
              cheias de líquido. São mais audíveis durante uma inspiração e não
              desaparecem com uma tosse. Podem ser encontradas em pacientes com edema
              pulmonar, fibrose, bronquite, bronquiectasia e som pneumonia. O de uma
              crepitação pode ser produzido esfregando-se uma mecha de cabelo contra os
              dedos.
            </p>
            <p>
              Subcrepitantes: Assemelha-se ao rompimento de pequenas bolhas, podendo ser
              auscultados nenhuma final da expiração e início da inspiração, não se
              modificam com uma tosse. Indicativos de pneumonia bronquite,
              broncopneumonia.
            </p>
            <p>
              [Roncos: Ocorrem em consequência da passagem de ar pelas vias aéreas
              estreitadas, repletas de secreções ou líquidos. São mais audíveis durante
              uma expiração e se modificam com uma tosse.
            </p>
            <p>
              Sibilos: São ruídos sussurrantes, decorrentes da passagem do ar por vias
              aéreas estreitadas. Quando muito intensos podem ser audíveis sem
              estetoscópio. São Associados broncoconstrição uma asma, bronquite.
            </p>
            <p>
              Atrito pleural: Decorrente de uma inflamação pleural filhos são do tipo
              Fricção causados por duas superfícies pleurais ressecadas que deslizam uma
              sobre a outra.
            </p>
            <p>
              Cornagem: É uma respiração ruidosa causada por uma obstrução ao nível da
              laringe e / ou traqueia. Os Filhos timpânicos podem ser, maciços e
              submaciços.
            </p>
            <p>Ausculta pulmonar anterior e ausculta pulmonar posterior.</p>
          </li>
          <li>
            <h4>Abdômen</h4>
            <div>
              <p>Inspeção:</p>
              <p>
                Observar a forma, abaulamento, retração, circulação colateral e
                localização da cicatriz umbilical.
              </p>
            </div>
            <div>
              <p>Ausculta:</p>
              <p>
                Através do estetoscópio detecta-se os ruídos peristálticos em toda
                extensão do abdome e possibilita a avaliação de toda sua frequência e
                características. Deve proceder a palpação e a percussão, pois testes podem
                alterar os sons intestinais;
              </p>
            </div>
            <div>
              <p>Palpação superficial:</p>
              <p>
                Utiliza-se as mãos espalmadas com as polpas digitais em movimentos
                rotativos e rápidos nas regiões do abdome. Permite reconhecer a
                sensibilidade, a integridade anatômica e a tensão da parede abdominal.
              </p>
            </div>
            <p>Intestinos</p>
            <div>
              <p>Palpação profunda:</p>
              <p>
                Somente o ceco e o sigmóide são palpáveis devido à sua localização sobre o
                músculo psoas. Posicione-se à direita do paciente com as mãos paralelas
                fletidas em garra. Na expiração penetrar com as mãos ao nível da cicatriz
                umbilical até o músculo psoas. Deslizar as mãos obliquamente em direção à
                região inguinal direita. Se o paciente referir dor após esas manobra,
                poderá apresentar sinal de Blumberg positivo. Repita no lado esquerdo para
                palpação do sigmóide, indicando presença de fecaloma. Esofageana - Tem a
                sensação de parada do bolo alimentar não esôfago.
              </p>
            </div>
          </li>
          <li>
            <h4>Genitália</h4>
            <p>
              Verificar presença de diurese e eliminações intestinais em pouca quantidade
              ou em grande. Ao examinar um Genitália (caso o cliente permita), manter uma
              terceira pessoa de preferência do mesmo sexo do cliente. Caso um cliente não
              permita ou por algum outro motivo que interfira o seu exame pode, assim você
              escrever: (SIC) que significa Informações colhidas Segundo.
            </p>
          </li>
          <li>
            <h4>Membros inferiores (E e D)</h4>
            <p>
              Verificar pele integra, edema, unhas quebradiças, sujidades, perfusão
              tissular eficaz ou não. planta do pé, verificar se está ressecada e outros.
            </p>
          </li>
        </ol>
      </article>
    </section>
  </div>
</template>

<script setup>
import { ref } from "vue";

const route = useRoute();
const router = useRouter();

// Inicialização do estado do histórico com campos específicos
const historico = ref({
  identificacao: {
    nome: "",
    idade: "",
    estado_civil: "",
    filhos: "",
    genero: "",
    escolaridade: "",
    etnia: "",
    ocupacao: "",
    naturalidade: "",
    procedencia: "",
    religiao: "",
    cuidador: "",
    grupo_sanguineo: "",
    fator_rh: "",
  },
  informacoes_doenca_tratamento: {
    motivo_internacao: "",
    diagnostico_medico: "",
    doencas_cronicas: "",
    fatores_risco: "",
    alergias_medicamentos: "",
    especificar: "",
    tratamentos_anteriores: "",
    cirurgias: "",
    outros_tratamentos: "",
  },
  socio_economicos_culturais: {
    moradia: "",
    animais_domesticos: "",
  },
  higiene: {
    habito_tomar_banho: "",
    atividade_fisica_trabalho: "",
    fumo: "",
    alcool: "",
    sono_repouso: "",
    exercicios_fisicos: "",
    eliminacao_urinaria: "",
    eliminacoes_intestinais: "",
  },
});

// Função para manipular o valor dos campos no objeto 'historico'
function atualizarCampo(categoria, campo, valor) {
  if (historico[categoria] && campo in historico[categoria]) {
    historico[categoria][campo] = valor;
  }
}

// Função para submissão dos dados do formulário
const submitForm = async () => {
  console.log("Histórico criado:", historico.value); // Verifica e exibe o histórico a ser criado

  const storedPacientes = sessionStorage.getItem("pacientes");

  if (!storedPacientes) {
    console.error("Nenhum paciente encontrado na sessionStorage.");
    return;
  }

  // Converte a lista de pacientes do sessionStorage
  const pacientes = JSON.parse(storedPacientes);

  // Obtém o ID do paciente da rota
  const pacienteId = parseInt(route.params.id);
  const pacienteIndex = pacientes.findIndex((item) => item.id === pacienteId);

  if (pacienteIndex === -1) {
    console.error("Paciente não encontrado.");
    return;
  }

  // Garante que o array de históricos exista
  if (!pacientes[pacienteIndex].historico) {
    pacientes[pacienteIndex].historico = []; // Inicializa como um array se não existir
  }

  // Adiciona o novo histórico ao array de históricos do paciente
  pacientes[pacienteIndex].historico = historico.value; // Adiciona o novo histórico ao array existente

  console.log(pacientes[pacienteIndex]);

  // Armazena os pacientes atualizados de volta na sessionStorage
  sessionStorage.setItem("pacientes", JSON.stringify(pacientes)); // Salva a lista atualizada de pacientes

  // Redireciona para a página do paciente
  router.push(`/pacientes/${pacienteId}/historico`);
};
</script>
<style scoped>
section.info {
  background-color: #f4f4f9;
  padding: 20px;
  border-radius: 8px;
  margin-block: 20px;
  font-family: Arial, sans-serif;
  line-height: 1.6;
}

section.info h1 {
  color: #2c3e50;
  text-align: center;
  margin-bottom: 20px;
  font-size: 28px;
}

section.info p {
  color: #34495e;
  margin-bottom: 15px;
}

section.info ul.list {
  list-style-type: disc;
  padding-left: 20px;
  margin-bottom: 20px;
}

section.info ul.list h3 {
  font-size: 20px;
  margin-bottom: 10px;
  color: #2980b9;
}

section.info ul.list li {
  margin-bottom: 10px;
  color: #7f8c8d;
}

section.info article {
  margin-top: 30px;
  padding-top: 20px;
  border-top: 2px solid #ecf0f1;
}

section.info article h3 {
  color: #2980b9;
  margin-bottom: 15px;
  font-size: 24px;
}

section.info article h4 {
  color: #16a085;
  margin-bottom: 10px;
}

section.info article p {
  margin-bottom: 15px;
  color: #2c3e50;
}

section.info article ul.list {
  list-style-type: circle;
  padding-left: 20px;
}

section.info article ul.list li {
  margin-bottom: 8px;
  color: #7f8c8d;
}

section.info ol.list {
  list-style-type: decimal;
  padding-left: 20px;
}

section.info ol.list li {
  margin-bottom: 15px;
  color: #34495e;
}

section.info ol.list h4 {
  color: #16a085;
  margin-bottom: 10px;
}

strong {
  color: #e74c3c;
}

@media (max-width: 768px) {
  section.info {
    padding: 15px;
    font-size: 14px;
  }

  section.info h1 {
    font-size: 24px;
  }

  section.info article h3 {
    font-size: 20px;
  }
}
</style>
