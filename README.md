# edu-slides :: A Simple and Obvious Latex Slide Maker

## Description:
The edu-slides LaTeX Style Package was designed to simplify the creation of slide decks 
for educational and academic purposes. This package was designed to support 
Generative AI workflows, through a template-driven design that allows seamless integration 
with AI-generated content. Slide content generated by AI tools can be directly 
injected into predefined templates with minimal human intervention, enabling rapid 
prototyping of presentations. 

The package includes predefined templates  for common slide types (e.g., cover, agenda, 
text-image, quotes), diverse layout options, and automated features. Users can define 
global parameters Through the use of key-value configurations (pgfkeys), including logos, 
colors, fonts, and layout dimensions, making it easy to tailor the presentation 
to institutional branding. 

The focus is on simplicity and obviousness ensuring that users—whether manually editing 
or leveraging AI outputs—can maintain a polished, professional appearance with minimal effort. 

## Getting Started:
Check the [main.tex](main.tex) template provided with this package.

![Quick Example](example-1.gif)

```
\documentclass[aspectratio=169]{beamer}
\usepackage{edu-slides}

\pgfkeys{
    /params/.is family,
    /params/.cd,
        % Logo
        logo/.initial           = images/fau-logo.png,
    %
        % Banner
        banner/.initial         = images/fau-banner.png,
    %            
        % Author
        author/.initial         = Dr. Fernando Koch,
        author/email/.initial   = kochf@fau.edu,
        author/url/.initial     = http://linkedin.com/in/fkoch,
    % 
        % Course
        course/.initial         = Principles of Software Engineering,
        course/code/.initial    = CEN~4010,
        course/logo/.initial    = images/cen4010-logo.png,
}


\begin{document}
     \slideCover{Lesson 1 \\ Introduction}
     \slideAgenda{
         \begin{itemize}
            \item Topic 1
            \item Topic 2
            \item Topic 3
         \end{itemize}
    }

    \slideTeleprompt{Topic 1}{\input{tests/text-1.txt}}
    \slideDouble{Topic 2}{\input{tests/text-1.txt}}{\input{tests/text-1.txt}}
    \slideTextImage{Topic 3}{tests/img-1.png}{\input{tests/text-1.txt}}
    \slideBackCover{}
\end{document}


```

## Disclaimer: 
GPT4o has been applied for the development of source code and documentation through this package

**Copyright 2024 Fernando Koch**
