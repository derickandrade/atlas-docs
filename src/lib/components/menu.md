Menu Um Menu exibe uma lista de opções, sugestões ou ações disponíveis. Ele se expande a partir de um controle (por exemplo, um botão, seletor ou entrada) após ser ativado por um usuário.

Visão Geral

Quando Usar o Menu

Use o componente Menu quando precisar exibir uma lista de opções selecionáveis em uma sobreposição temporária, tipicamente ancorada a um trigger (gatilho) como um botão ou input. É comumente usado dentro de outros componentes como dropdowns, campos de seleção (select inputs) ou botões de ação.

Use-o quando:

    Você deseja mostrar opções agrupadas ou contextuais acionadas por uma interação.

    Você precisa de sobreposições leves, acessíveis via teclado e visualmente.

Evite usá-lo:

    Quando precisar de elementos de navegação persistentes (use uma Navigation Bar ou Tabs).

    Para interações complexas ou com várias etapas (use um Dialog ou Popover em vez disso).

Sobre o Menu

Defina a anatomia do componente listando todos os elementos ou subcomponentes que o compõem. Forneça uma definição para cada elemento e inclua tantos Do's e Don'ts quanto necessário para delinear as melhores práticas para usar o componente de forma eficaz.

1. Menu Item

Um elemento acionável dentro do Menu. Pode ser um link, botão ou opção.
Prática	Descrição
✅ Do	Mantenha os Menu Items curtos, claros e interativos.
✅ Do	Use ícones ou badges para adicionar contexto visual sem sobrecarregar.
❌ Don't	Evite colocar conteúdo não interativo aqui (como parágrafos ou grandes blocos de texto).
❌ Don't	Não use Menu Items para iniciar ações complexas que exijam validação ou feedback extenso.

2. Menu Divider (Opcional)

Separa visualmente grupos de Menu Items para melhor organização.
Prática	Descrição
✅ Do	Use-o para quebrar menus longos em seções lógicas.
❌ Don't	Não use em excesso; inclua somente se o agrupamento adicionar clareza ou contexto.

Exemplos

Uso Básico: Menu de Ações

Descrição do Exemplo: Este exemplo demonstra o uso básico do componente <AtlMenu> recebendo uma prop items (itens) com dados estruturados. Os itens incluem uma ação padrão, uma ação com badge (badgeNumber) e chevron para indicar sub-menu ou navegação, e uma ação desabilitada (disabled: true). O menu é acionado por um elemento não visível no código de exemplo, mas que seria o componente AtlButton ou similar.
TypeScript

const menuItems = [
    {
        label: 'Action',
        href: '#',
        icon: null,
        tiptext: 'Tooltip action example',
        tipicon: null,
        badgeNumber: 100,
        chevron: false,
        disabled: false,
        target: '_blank'
    },
    {
        label: 'Action', // Exemplo 2: Com badge e chevron
        href: '#',
        badgeNumber: 20,
        chevron: true
    },
    {
        label: 'Disabled Action',
        href: '#',
        disabled: true // Exemplo 3: Item desabilitado
    }
];

// Uso no template:
<AtlMenu items={menuItems}></AtlMenu>

Implementação Técnica

Navegação por Teclado

Tecla	Função
Tab	Move o foco entre o trigger e os próximos elementos focáveis fora do Menu.
Enter / Espaço	Abre o Menu se o trigger estiver focado.
Seta para Baixo / Seta para Cima	Navega entre os Menu Items.
Esc	Fecha o Menu.
Enter	Seleciona o Menu Item focado.

Link para o Issue correspondente no GitHub para Revisão da Equipe de Design Systems antes da publicação:

[Link to GitHub Issue]