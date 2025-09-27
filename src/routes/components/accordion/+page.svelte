<svelte:head>
	<title>Accordion</title>
	<meta name="Accordion" content="Accordion component" />
</svelte:head>

<main>
	<h1>Accordion</h1>
	<p>
		An Accordion is an expandable and collapsible section of content, often featured in a vertically stacked list with other Accordions. Accordions are commonly used to organize content into collapsed sections, making the interface easier to navigate.		
	</p>
    <img src="" alt="Imagem de um Accordion" />
    <div id="div-line"></div>

    <h2 id="overview">Overview</h2>

    <h3>When to use accordion</h3>
    <p>
        Use the Accordion component when you need to organize blocks of content into sections. Avoid using an Accordion when the user needs to read the content by default. In this case, use another component or group of elements instead.
        Expanded Accordion content can be as long as needed, and the type of content can vary contextually. Headings should be used to label each section of content.
    </p>

    <h3>About Accordion</h3>
    <p>Accordion includes the following elements.</p>
    <h4>Title</h4>
    <p>
        The title or label provides a brief description of the Accordion's content. Pressing on this section expands or collapses the Accordion.
    </p>
    <ul class="list-dos">
        <li>
            <span class="bold">Do:</span> Customize the title to other styles by applying any of the existing fonts, text sizes or formats defined in our font design tokens.
        </li>
        <li>
            <span class="bold">Do:</span> Always make sure to emphasize the label more prominently than the expanded content.
        </li>
        <li>
            <span class="bold">Don't:</span> Avoid customizing the label color as it may lead to contrast issues with the various states of the Accordion.
        </li>
        <li>
            <span class="bold">Don't:</span>  Avoid combining different text styles within the labels of the same Accordion group.
        </li>
        <li>
            <span class="bold">Don't:</span> Avoid including links in the Accordion label.
        </li>
    </ul>

    <h4>Content</h4>
    <p>The expanded content within the Accordion can include paragraph text, links, images, videos, tables, or form items. There are no restrictions on the minimum or maximum amount of content that can be included in the expanded section.</p>
    <ul class="list-dos">
        <li>
            <span class="bold">Do:</span> Use sub-headers to represent different subsections within Accordion content.
        </li>
        <li>
            <span class="bold">Don't:</span> Avoid nesting additional Accordions within an Accordion item to create subsections.
        </li>
    </ul>

    <div id="div-line"></div>

    <h2 id="examples">Examples</h2>
    <h3>Basic usage</h3>
    <img src="" alt="Imagem">

    <div id="div-line"></div>

    <h2 id="keyboard-navigation">Keyboard navigation</h2>
    <p>Inserir a tabela</p>

	<aside>
		<ul>
            <li><a href="#overview">Overview</a></li>
            <li><a href="#examples">Examples</a></li>
            <li><a href="#keyboard-navigation">Keyboard navigation</a></li>
        </ul>
	</aside>
	
</main>
