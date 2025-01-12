# edu-slides :: A Simple and Obvious Latex Slide Maker

## Description:
This package is being developed to simplify the creation of educational slide decks 
for academic purposes.  The solution is structured around the idea of 'rules for creating slides'. This aims to to support the integration of  Generative AI workflows. 

The focus is on simplicity, obviousness, and machine-learning enablement, ensuring a polished, 
professional appearance with minimal effort. 

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



