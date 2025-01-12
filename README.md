# edu-slides :: A Simple and Obvious Latex Slide Maker

## Description:
This package is being developed to simplify the creation of educational slide decks 
for academic purposes.  The solution is structured around the idea of 'rules for creating slides'. This aims to to support the integration of  Generative AI workflows. 

The focus is on simplicity, obviousness, and machine-learning enablement, ensuring a polished, 
professional appearance with minimal effort. 

## Templates

The source code documentation describe the templates as 'rules' that can be used for Generative AI (check for comments tagged with @template). The templates are structured in two groups: (Group 1) Structured Templates, for composed slides to simplify the work, and; (Group 2) Working Templates, for configuration slides with multiple parameters and variations.

### (Group 1) Structured Templates

```
%% \slideCover{TITLE}
%% Generates the opening slide for the deck with TITLE
```

```
%% slideAgenda{TOPICS}
%% Generates an Agenda with TOPICS
```

```
%% \slideBackCover
%% Generates the closing slide for the deck
```

```
%% \slideDivider{SECTION_TITLE}
%% Generates a DIVIDER with a SECTION_TITLE to separate sections
```

```
%% \slideQA{QUESTION}{ANSWER}
%% Generates a sldie structured for Question and Answer
```

```
%% \slideLiterature[title=TITLE, image=COVER, link=LINK]{CONTENT}
%% Generates a slide to present a book with TITLE, COVER, and CONTENT.
%% Optionally provide LINK to book content.
```

### (Group 2) Working Templates

```
%% \slideSimple[type=TYPE, title=TITLE, font=FONT]{CONTENT}
%% Generates a slide with one column of given content TYPE (text(default), image, diagram, import).
%% Apply optional TITLE.
%% Apply provided CONTENT; if type=text, apply FONT (small, body, title, big) for text content.
```

```
%% \slideDouble[type/1=TYPE, type/2=TYPE, font/1=FONT, font/2=font, title=TITLE]{CONTENT_LEFT}{CONTENT_RIGHT}
%% Generates a slide with two columns.
%% Each column defined with a given content TYPE (text(default), image, diagram, import), and FONT (small, body, large, big)
%% Add optional TITLE.
```

```
%% \slideExplanation[type=ORDER, type/1=TYPE, type/2=TYPE, font/1=FONT, font/2=font, title=TITLE]{CONTENT_LEFT}{CONTENT_RIGHT}
%% Specalization of \slideDouble with columns distributed as 2/5 and 3/5 of the slide space.
%% type=reversed applies 3/5 and 2/5 column distribution.
%% Other parameters like \slideDouble
```

```
%% \slideMultiple[type=TYPE, title=TITLE, title/1=Title1, ..., title/N=TitleN, content/1=!text-1]
%% Generates a slide with multiple columns.
%% TYPE (text(default), image, diagram) defines the type of each column's title
%% TITLE (optional) defines the slide TITLE
%% title/n defines the TITLE_n for column N
%% text/n defines the text for column N
```

## Getting Started

We provide a 'getting started' example in the [main.tex](./main.tex), which will generate the ([PDF](./main.pdf) attached).

The code below presents the steps to create a very simple slide deck.


```
\documentclass[aspectratio=169]{beamer}
\usepackage{edu-slides}

%%
%% (1) Define the presentation parameters here
%%
\pgfkeys{
    /params/.is family,
    /params/.cd,
        % Author
        author/.initial         = Dr. Fernando Koch,
        author/email/.initial   = kochf@fau.edu,
        author/url/.initial     = http://linkedin.com/in/fkoch,
    % 
        % Course
        course/.initial         = Principles of Software Engineering,
        course/code/.initial    = CEN~4010,
        course/logo/.initial    = logos/cen4010-logo.png,
    %   
        % Debug
        debug/import/.initial   = false,     %% detail process of finding and importing files
        debug/layout/.initial   = false,     %% mark positions, so you can adjust the layouts
        debug/compTime/.initial = true,     %% add marker with time of compilation on Cover and BackCover
}


%%
%% (2) Configure the sequence of slides applying our easy-to-use templates
%% (Note: the complete set of templates can be tested through main.tex)
%%
\begin{document}
    % Open slide deck
    \slideCover{Hello World!}

    % Template for Agenda
    \slideAgenda{Topic 1 \\ Topic 2}

    % load text from text-1 from possible text locations
    \slideSimple[title=Topic 1]{Some text here} 

    % load TIKz diagram tree-1 and image img-1
    \slideDouble[type/1=diagram, type/2=image, title=Topic 2]{tree-1}{img-1} 

    % Closing slide
    \slideBackCover
\end{document}

```



