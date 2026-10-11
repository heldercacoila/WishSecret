Gera uma aplicação web completa (Single Page Application) em HTML5, Tailwind CSS (via CDN) e JavaScript puro (ES6+) para uma plataforma de **Wishlists Colaborativas com "Modo Mistério" (Segredo do Dono)**.

### Requisitos Técnicos Obrigatórios:
1. **Estrutura de Ficheiro Único (index.html)**: Tudo deve estar contido num único ficheiro HTML limpo, com CSS incorporado e scripts no final para evitar erros de carregamento, ecrãs brancos ou problemas de caminhos de módulos ES6.
2. **Frameworks e Bibliotecas (via CDN)**:
   - Tailwind CSS (para um design moderno, responsivo e elegante estilo Apple/Notion).
   - FontAwesome ou Lucide Icons (para ícones intuitivos).
   - Firebase SDK (Firestore) opcional com fallback automático para `localStorage` para garantir que a aplicação nunca falha caso as chaves do Firebase não estejam configuradas ou haja falhas de rede.
3. **Design & Responsividade**:
   - Mobile-first, interface limpa, tons suaves (pastel/neutros), cantos arredondados, sombras subtis e transições suaves (`transition-all`).
   - Suporte completo para redimensionamento em telemóveis, tablets e desktops.

---

### Funcionalidades Detalhadas a Implementar:

#### 1. Ecrã Inicial / Home:
- Permite **Criar uma Nova Wishlist** (inserindo o Nome da Lista, Descrição e opcionalmente uma password de dono).
- Permite **Entrar numa Lista Existente** através de um ID/Código único ou link partilhado.

#### 2. Gestão da Lista (Visualização por Abas/Budgets):
- A lista de desejos deve estar organizada em categorias de orçamento (`Até 20€`, `20€ - 50€`, `50€ - 100€`, `Mais de 100€` ou "Todos").
- Cada item de desejo deve conter:
  - Foto do produto (com suporte a colar URL de imagem e pré-visualização imediata).
  - Nome do produto.
  - Preço aproximado.
  - Link direto para a loja (clicável).
  - Notas adicionais (tamanho, cor, preferência).

#### 3. Os Dois Modos de Utilização (O Core da App):
- **Modo Dono (Dono da Lista)**:
  - Pode adicionar, editar e apagar itens da sua própria lista.
  - **REQUISIÇÃO CRÍTICA**: O dono **NUNCA** pode saber se um item foi reservado ou por quem foi reservado. A interface do dono não deve mostrar quaisquer botões de reserva, contadores de reservas ou nomes de compradores.
- **Modo Convidado / Amigo**:
  - Acede através de um link de partilha (ex: `?list=ID_DA_LISTA`).
  - Vê todos os desejos organizados por orçamento.
  - Vê o botão **"Reservar Oferta"**. 
  - Ao clicar em reservar, o convidado insere o seu nome (opcional) e o item fica marcado como "Reservado" para os outros convidados (evitando prendas repetidas), mas **invisível/sem alteração aparente para o dono**.
  - O convidado pode cancelar a sua própria reserva se mudar de ideias.

#### 4. Partilha e Persistência:
- Botão rápido de "Copiar Link para Partilhar".
- Sistema de armazenamento robusto: Tenta sincronizar com o Firebase Firestore; se falhar ou se estiver offline, usa o `localStorage` do navegador com chaves únicas por lista para garantir resiliência a 100% (evitando o erro do ecrã branco).

### Robustez do Código:
- Envolve toda a lógica de arranque e manipulação de dados em blocos `try / catch`.
- Garante tratamento de erros visuais (mensagens de aviso amigáveis em toasts ou modais, nunca deixando a página em branco).
- Adiciona um indicador de carregamento (spinner) enquanto os dados da lista são obtidos.
