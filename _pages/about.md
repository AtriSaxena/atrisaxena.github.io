---
permalink: /about/
title: "About"
excerpt: "All about me."
---

Hi there, I'm Atri Saxena, :)

I post graduated from M.Tech in Information Security from NIT Jalandhar, Jalandhar. My research was mainly focused on Deep learning and Computer Vision.

I'm a big fan of Automation, Machine Learning and Computer Vision. I'm doing some works on Machine Learning and Computer Vision. I'm also maintaining this blog to share my knowledge about ML and CV, as well as my work on both fields. You can find all my undergoing projects here on github: [My GitHub](https://github.com/atrisaxena).


Hope this blog help with your learning. And don't hesitate to drop me a line. I'll reply as soon as I can, promise!

%-----------------------------------------------------------------------------------------------------------------------------------------------%
%	The MIT License (MIT)
%
%	Copyright (c) 2015 Jan Küster
%
%	Permission is hereby granted, free of charge, to any person obtaining a copy
%	of this software and associated documentation files (the "Software"), to deal
%	in the Software without restriction, including without limitation the rights
%	to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
%	copies of the Software, and to permit persons to whom the Software is
%	furnished to do so, subject to the following conditions:
%	
%	THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
%	IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
%	FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
%	AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
%	LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
%	OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
%	THE SOFTWARE.
%	
%
%-----------------------------------------------------------------------------------------------------------------------------------------------%


%============================================================================%
%
%	DOCUMENT DEFINITION
%
%============================================================================%

%we use article class because we want to fully customize the page and dont use a cv template
\documentclass[10pt,A4]{article}	


%----------------------------------------------------------------------------------------
%	ENCODING
%----------------------------------------------------------------------------------------

%we use utf8 since we want to build from any machine
\usepackage[utf8]{inputenc}		
\usepackage{tikz} 

%----------------------------------------------------------------------------------------
%	LOGIC
%----------------------------------------------------------------------------------------

% provides \isempty test
\usepackage{xifthen}
\usepackage{afterpage}
%----------------------------------------------------------------------------------------
%	FONT
%----------------------------------------------------------------------------------------

% some tex-live fonts - choose your own

%\usepackage[defaultsans]{droidsans}
%\usepackage[default]{comfortaa}
%\usepackage{cmbright}
%\usepackage[default]{raleway}
%\usepackage{fetamont}
\usepackage[default]{gillius}
%\usepackage[light,math]{iwona}
%\usepackage[thin]{roboto} 

% set font default
\renewcommand*\familydefault{\sfdefault} 	
\usepackage[T1]{fontenc}

% more font size definitions
\usepackage{moresize}		

\usepackage{fontawesome}
%----------------------------------------------------------------------------------------
%	PAGE LAYOUT  DEFINITIONS
%----------------------------------------------------------------------------------------

%debug page outer frames
%\usepackage{showframe}			


%define page styles using geometry
\usepackage[a4paper]{geometry}		

% for example, change the margins to 2 inches all round
\geometry{top=1cm, bottom=-.6cm, left=0.4cm, right=1cm} 	


%less space between header and content
\setlength{\headheight}{-5pt}		


%customize entries left, center and right
%\lhead{}
%\chead{ \small{Jan Küster  $\cdot$ Consultant and Software Engineer $\cdot$  Bremen, Germany  $\cdot$  \textcolor{sectcol}{\textbf{info@jankuester.com}}  $\cdot$ +49 176 313 *** **}}
%\rhead{}


%indentation is zero
\setlength{\parindent}{0mm}

%----------------------------------------------------------------------------------------
%	TABLE /ARRAY DEFINITIONS
%---------------------------------------------------------------------------------------- 

%for layouting tables
\usepackage{multicol}			
\usepackage{multirow}

%extended aligning of tabular cells
\usepackage{array}

\newcolumntype{x}[1]{%
>{\raggedleft\hspace{0pt}}p{#1}}%


%----------------------------------------------------------------------------------------
%	GRAPHICS DEFINITIONS
%---------------------------------------------------------------------------------------- 

%for header image
\usepackage{graphicx}

%for floating figures
\usepackage{wrapfig}
\usepackage{float}
%\floatstyle{boxed} 
%\restylefloat{figure}

%for drawing graphics		
\usepackage{tikz}				
\usetikzlibrary{shapes, backgrounds,mindmap, trees}


%----------------------------------------------------------------------------------------
%	Color DEFINITIONS
%---------------------------------------------------------------------------------------- 
\usepackage{transparent}
\usepackage{color}

%accent color
\definecolor{complcol}{RGB}{250,150,10}

%dark background color
\definecolor{bgcol}{RGB}{110,110,110}

%light background / accent color
\definecolor{softcol}{RGB}{225,225,225}

\definecolor{sectcol}{RGB}{0,120,150}


%Package for links, must be the last package used
\usepackage[hidelinks]{hyperref}

%============================================================================%
%
%
%	DEFINITIONS
%
%
%============================================================================%
\newcommand{\cvtags}[1]{\tikz[baseline=(X.base)]\node [draw=white,fill=complcol,rounded corners,inner xsep=1ex,inner ysep =0.75ex,text height=1.5ex,text depth=.25ex, rounded corners=3pt] (X) {#1};}


% returns minipage width minus two times \fboxsep
% to keep padding included in width calculations
\newcommand{\mpwidth}{\linewidth-\fboxsep-\fboxsep}


% Change the bullets for itemize and rating marker
% for \cvskill if you want to

%----------------------------------------------------------------------------------------
% 	ARROW GRAPHICS in Tikz
%----------------------------------------------------------------------------------------

% a six pointed arrow poiting to the left
\newcommand{\tzlarrow}{(0,0) -- (0.2,0) -- (0.3,0.2) -- (0.2,0.4) -- (0,0.4) -- (0.1,0.2) -- cycle;}	

% include the left arrow into a tikz picture
% param1: fill color
%
\newcommand{\larrow}[1]
{\begin{tikzpicture}[scale=0.58]
	 \filldraw[fill=#1!100,draw=#1!100!black]  \tzlarrow
 \end{tikzpicture}
}

% a six pointed arrow poiting to the right
\newcommand{\tzrarrow}{ (0,0.2) -- (0.1,0) -- (0.3,0) -- (0.2,0.2) -- (0.3,0.4) -- (0.1,0.4) -- cycle;}

% include the right arrow into a tikz picture
% param1: fill color
%
\newcommand{\rarrow}
{\begin{tikzpicture}[scale=0.7]
	\filldraw[fill=sectcol!100,draw=sectcol!100!black] \tzrarrow
 \end{tikzpicture}
}

%----------------------------------------------------------------------------------------
%	custom sections
%----------------------------------------------------------------------------------------

% create a coloured box with arrow and title as cv section headline
% param 1: section title
%
\newcommand{\cvsection}[1]
{
\colorbox{sectcol}{\mystrut \makebox[1\mpwidth][l]{
\larrow{bgcol} \hspace{-8pt} \larrow{bgcol} \hspace{-8pt} \larrow{bgcol} \textbf{\textcolor{white}{\uppercase{#1}}}\hspace{4pt}
}}\\
}

% create a coloured arrow with title as cv meta section section
% param 1: meta section title
%
\newenvironment{metasection}[1] {
	\vspace{6pt}
	\begin{center}
		\textcolor{white}{\large{\uppercase{#1}}}\\
	\normalsize
	\parbox{0.7\mpwidth}{\textcolor{white}	\hrule}
}{\end{center}}

%----------------------------------------------------------------------------------------
%	 CV EVENT
%----------------------------------------------------------------------------------------

% creates a stretched box as cv entry headline followed by two paragraphs about 
% the work you did
% param 1:	event time i.e. 2014 or 2011-2014 etc.
% param 2:	event name (what did you do?)
% param 3:	institution (where did you work / study)
% param 4:	what was your position
% param 5:	some words about your contributions
%
\newcommand{\cvevent}[5]
{
\vspace{6pt}
	\begin{tabular*}{1\mpwidth}{p{150pt}  x{210pt}}
 	\textcolor{black}{\textbf{#2}} & \textcolor{complcol}{#3}, \textcolor{bgcol}{#1} 

	\end{tabular*}
\vspace{-12pt}
\textcolor{softcol}{\hrule}
\vspace{7pt}
	\begin{tabular*}{0.5\mpwidth}{p{\mpwidth}}
\larrow{softcol}  #4\\[3pt]
\larrow{softcol}  #5\\[6pt]
	\end{tabular*}

}

% creates a stretched box as 
\newcommand{\cveventmeta}[2]
{
	\mbox{\mystrut \hspace{87pt}\textit{#1}}\\
	#2
}

%----------------------------------------------------------------------------------------
% CUSTOM STRUT FOR EMPTY BOXES
%----------------------------------------- -----------------------------------------------
\newcommand{\mystrut}{\rule[-.3\baselineskip]{0pt}{\baselineskip}}

%----------------------------------------------------------------------------------------
% CUSTOM LOREM IPSUM
%----------------------------------------------------------------------------------------
\newcommand{\lorem}
{Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec a diam lectus.}


% use to vertically center content
% credits to: http://tex.stackexchange.com/questions/7219/how-to-vertically-center-two-images-next-to-each-other
\newcommand{\vcenteredinclude}[1]{\begingroup
\setbox0=\hbox{\includegraphics{#1}}%
\parbox{\wd0}{\box0}\endgroup}

% use to vertically center content
% credits to: http://tex.stackexchange.com/questions/7219/how-to-vertically-center-two-images-next-to-each-other
\newcommand*{\vcenteredhbox}[1]{\begingroup
\setbox0=\hbox{#1}\parbox{\wd0}{\box0}\endgroup}

%----------------------------------------------------------------------------------------
%	ICON-SET EMBEDDING
%---------------------------------------------------------------------------------------- 

% at this point we simplify our icon-embedding by simply referring to a set of png images.
% if you find a good way of including svg without conflicting with other packages you can
% replace this part
\newcommand{\icon}[3]{\makebox(#2, #2){\textcolor{#3}{\csname fa#1\endcsname}}}	%icon shortcut
\newcommand{\icontext}[4]{ 						%icon with text shortcut
	\vcenteredhbox{\icon{#1}{#2}{#4}} \vcenteredhbox{\textcolor{#4}{#3}}
}
\newcommand{\iconhref}[5]{ 						%icon with website url
    \vcenteredhbox{\icon{#1}{#2}{#5}} \href{#4}{\textcolor{#5}{#3}}
}

\newcommand{\iconemail}[5]{ 						%icon with email link
    \vcenteredhbox{\icon{#1}{#2}{#5}} \href{mailto:#4}{\textcolor{#5}{#3}}
}



%============================================================================%
%
%
%
%	DOCUMENT CONTENT
%
%
%
%============================================================================%
\begin{document}
\fcolorbox{white}{white}{\begin{minipage}[c][0.95\textheight][t]{0.69\linewidth}
%---------------------------------------------------------------------------------------
%	TITLE HEADLINE
%----------------------------------------------------------------------------------------
\vspace{-3pt}
% use this for multiple words like working titles etc.
%\hspace{-0.25\linewidth}\colorbox{bgcol}{\makebox[1.5\linewidth][c]{\hspace{46pt}\HUGE{\textcolor{white}{\uppercase{M.Sc. Jan Küster}} } \textcolor{sectcol}{\rule[-1mm]{1mm}{0.9cm}} \parbox[b]{5cm}{   \large{ \textcolor{white}{{IT Consultant}}}\\
% \large{ \textcolor{white}{{JS Fullstack Engineer}}}}
%}}

% use this for single words, e.g. CV or RESUME etc.
\colorbox{bgcol}{\makebox[\mpwidth][c]{\HUGE{\textcolor{white}{\uppercase{Atri saxena}} } \textcolor{sectcol}{\rule[-1mm]{1mm}{0.9cm}} \HUGE{\textcolor{white}{\uppercase{Resume}} } }}

%----------------------------------------------------------------------------------------
%	HEADER IMAGE
%----------------------------------------------------------------------------------------


%\hspace{-1.6cm}
%\includegraphics[trim= 0 250 0 270,clip,width=1\linewidth+3.1cm]{myfoto.jpg}	%trimming relative to image size!
%\includegraphics[trim= 350 150 0 200, clip ,width=\linewidth]{myfoto.jpg}	%trimming relative to image size

%---------------------------------------------------------------------------------------
%	SUMMARY
%----------------------------------------------------------------------------------------
%\transparent{0.85}%
%\vspace{-130pt}
%\hspace{0.4\linewidth}
%\colorbox{bgcol}{
%	\parbox{0.5\linewidth}{
%		\transparent{1}%
%		\begin{center}
%		\larrow{sectcol}\larrow{sectcol}\textcolor{white}{I create awesome resume templates in %LaTeX for everyone. Besides that I am working at the University of Bremen and engineer %fullstack JS applications with Meteor.}
%		\end{center}
%	}
%}
%\vspace{50pt}

%============================================================================%
%
%	CV SECTIONS AND EVENTS (MAIN CONTENT)
%
%============================================================================%

%---------------------------------------------------------------------------------------
%	STATUS
%----------------------------------------------------------------------------------------
\cvsection{Status}

Hey, I am currently working as Software Engineer. I have an interest in Machine Learning, Cloud Technology and API building. I am also passionate about writing blogs.

\vspace{10pt}


%---------------------------------------------------------------------------------------
%	EXPERIENCE
%----------------------------------------------------------------------------------------
\cvsection{Experience}

\cvevent{April 2019 - Present}{SFO Technologies}{Software Engineer}{Data Analysis and getting insights.}{Applying various Machine Learning and Deep Learning Techniques on NLP data.}


\cvevent{August 2019-March 2020}{Cankids}{Assistant Manager}{Worked on Salesforce Development and Administration.}{Cleaning and analysis of data. }

\vspace{10pt}


%---------------------------------------------------------------------------------------
%	EDUCATION SECTION
%--------------------------------------------------------------------------------------
\cvsection{Education}

\cvevent{2017-19}{Post Graduate}{NIT Jalandhar}{M.Tech in Information Security with 8.02 CGPA out of 10.}{Master Thesis: An Effective Animal Detection Approach based on Deep Learning.}

%\textcolor{softcol}{\hrule}

%
\cvevent{2012-16}{Graduation}{Meerut Institute of Technology}{B.Tech in Computer Science with 68.92 \%.}{A NewsMemoria Website in PHP to create grammatical question from News.}

%\textcolor{softcol}{\hrule}

%
\cvevent{2011 - 2012}{Intermediate}{S.K.D Academy, Lucknow}{Intermediate from ICSE Board with 64 \%.}{Gained interest in Computer Science \& Programming.}

%\textcolor{softcol}{\hrule}

%
\cvevent{2009 - 2010}{HighSchool}{Lucknow Public School, Lucknow}{High School from UP Board with 70.33 \%.}{Best in Computer Award.}

\vspace{10pt}

\cvsection{Projects}

\cvevent{April 2020-June 2020}{Hospital Locator Chatbot}{Rasa Chatbot}{Helps to Locate the hospitals in India using Rasa framework.}{Deployed on Google Compute using Docker Compose.}

\cvevent{Feb 2020-Mar 2020}{Salesforce Email Lightning App}{Salesforce}{Salesforce lightning app to send custom Email with attachment.}{Using Salesforce Apex, javascipt.}

\cvevent{Dec 2019-Jan 2020}{Object Detection REST API}{API}{Django REST API to get object detection with API Token Auth.}{Deployment on Google Cloud Kubernetes.}

\cvevent{June 2019-July 2019}{SSD: Object Detection}{Web App}{Web App written in python using the Django framework.}{Deployment of SSD Object detection model on Google Cloud using Docker Container.}

\end{minipage}}
\fcolorbox{white}{sectcol}{\begin{minipage}[c][0.95\textheight][t]{0.33\linewidth}
\begin{metasection}{Contact}

	\icontext{MapMarker}{12}{New Delhi, India}{white}\\[6pt]
	\icontext{MobilePhone}{12}{+91 9336355386}{white}\\[6pt]
	\iconemail{Send}{12}{atrisaxena2@gmail.com}{}{white}\\[6pt]
	\iconhref{MousePointer}{12}{http://atrisaxena.github.io/}{www.atrisaxena.github.io}{white}\\[6pt]
	\iconhref{Github}{12}{https://github.com/atrisaxena}{https://github.com/atrisaxena}{white}\\[6pt]
	\iconhref{Linkedin}{12}{https://www.linkedin.com/in/atrisaxena/}{https://www.linkedin.com/in/atrisaxena/}{white}\\[6pt]

\end{metasection}
	
%----------------------------------------------------------------------------------------
%	META SECTION
%----------------------------------------------------------------------------------------

\begin{metasection}{Technologies}

\icontext{Code}{12}{Software Development}{white}\\
\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\icon{Star}{12}{white}\\[6pt]

\icontext{Code}{12}{Machine Learning/Deep Learning}{white}\\
\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\icon{Star}{12}{white}\\[6pt]

\icontext{Code}{12}{Cloud}{white}\\
\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\\[6pt]


\icontext{Code}{12}{Salesforce}{white}\\
\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\\[6pt]

\icontext{Code}{12}{Docker}{white}\\
\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\\[6pt]

\icontext{Code}{12}{Apache Beam}{white}\\
\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\\[6pt]

\icontext{Code}{12}{Django REST API}{white}\\
\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\\[6pt]


\end{metasection}
\begin{metasection}{Programming Languages}
	
\icontext{Code}{12}{Python}{white}\\
\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\\[6pt]

\icontext{Code}{12}{Javascript}{white}\\
\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\\[6pt]

\icontext{Code}{12}{C}{white}\\
\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\icon{Star}{12}{white}\\[6pt]


\icontext{Code}{12}{PHP}{white}\\
\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\\[6pt]


\end{metasection}

\begin{metasection}{Deep Learning Framework}

	\icontext{Code}{12}{TensorFlow}{white}\\
	\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\\[6pt]

	\icontext{Code}{12}{PyTorch}{white}\\
	\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\\[6pt]

	\icontext{Code}{12}{Keras}{white}\\
	\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\icon{Star}{12}{white}\icon{Star}{12}{white}\\[6pt]
	


\end{metasection}



\end{minipage}}

%---------------------------------------------------------------------------------------
%	QR CODE (optional)
%----------------------------------------------------------------------------------------

%\vspace{12pt}
%\begin{center}
%\includegraphics[width=0.35\mpwidth]{qrcode}
%\end{center}



%-------------------------------------------------------------------------------------------------
%	ARTIFICIAL FOOTER (fancy footer cannot exceed linewidth) 
%--------------------------------------------------------------------------------------------------

%\null
%\vspace*{\fill}
%\hspace{-0.25\linewidth}\colorbox{bgcol}{\makebox[1.5\linewidth][c]{\mystrut \small \textcolor{white}{Coypright 2018 jkuester@uni-bremen.de} $\cdot$ \textcolor{white}{licensed unter MIT license}}}

%============================================================================%
%
%
%
%	DOCUMENT END
%
%
%
%============================================================================%

\newpage

\vspace{9pt}
\fcolorbox{white}{white}{\begin{minipage}[c][0.95\textheight][t]{0.69\linewidth}


\cvevent{Dec 2017-Jan 2018}{Twitter Semantic NLTK}{Machine Learning}{Access Tweets from Twitter API and do Semantic Analysis using NLTK and Machine Learning Algorithm.}{Using python and NLTK package for language processing and Machine learning algorithms.}

\cvevent{Sept 2017-Nov 2018}{Cryptographic Algorithms}{Security}{Implementation of some Symmetric \& Asymmetric encryption algorithms.}{Using Python as language with github link: \href{https://github.com/AtriSaxena/CRYPTOGRAPHY}{https://github.com/AtriSaxena/CRYPTOGRAPHY}}

\cvevent{2015 - 2016}{News Memoria}{Web Project}{To access data using RSS feeds and show news. Also made English questions from it.}{Using PHP, MySQL in backend and HTML, css, javascipt in front end.}
\vspace{9pt}


%---------------------------------------------------------------------------------------
%	EXPERIENCE
%----------------------------------------------------------------------------------------

%---------------------------------------------------------------------------------------
%	EDUCATION SECTION
%--------------------------------------------------------------------------------------
\cvsection{Achievements}
\begin{itemize}
	\item Udacity Nano Degree \textbf{"Natural Language Processing", May 2020.}
	\item Coursera Specialization \textbf{"Advance Machine Learning with Tensorflow on Google Cloud Platform", April 2020.}
	\item Coursera Specialization \textbf{"Machine Learning with TensorFlow on Google Cloud Platform", August 2019.}
	\item Cracked GATE Exam in 2017 with AIR 5589 Rank.
	\item Organized 2 days Machine Learning workshop as a Google MLCC Facilitator.
	\item \textbf{Publication:} Atri Saxena, DK Gupta and Samayveer Singh “An Animal Detection and Collision Avoidance System Using Deep Learning” First International Conference on Advanced Communication \& Computational Technology (ICACCT 2019), Springer LNCS (Accepted)
	\item Cracked GATE Exam in 2017 with AIR 5589 Rank.
	\item \textbf{"Best in Computer"} in class 9th.

\end{itemize}

\end{minipage}}
\fcolorbox{white}{sectcol}{\begin{minipage}[c][0.95\textheight][t]{0.33\linewidth}

	\begin{metasection}{Tools}

		\textcolor{white}{
		\icontext{Code}{12}{VS Code}{white} \icontext{CodeFork}{12}{Anaconda}{white}\\[6pt]
		\icontext{Terminal}{12}{Terminal}{white}  \icontext{PaintBrush}{12}{Latex}{white} 
		\icontext{Code}{12}{Pytorch}{white}
		}
		\end{metasection}
		
		\begin{metasection}{Operating Systems}
		
		\textcolor{white}{\LARGE{\icon{Linux}{24}{white}  \icon{Windows}{24}{white}}}
		
		\end{metasection}


	\begin{metasection}{Activities}

		\textcolor{white}{\LARGE{\icon{Gamepad}{24}{white} \icon{Headphones}{24}{white}  \icon{Bicycle}{24}{white}}}
	\end{metasection}

\begin{metasection}{Languages}

	\icontext{Code}{12}{English}{white}\\
	\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\icon{Star}{12}{white}\\[6pt]

	\icontext{Code}{12}{Hindi}{white}\\
	\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{complcol}\icon{Star}{12}{white}\icon{Star}{12}{white}\\[6pt]


\end{metasection}

\begin{metasection}{Strengths}

	\cvtags{HardWorking} \cvtags{Dedication} 

	\vspace{5pt}
	
	\cvtags{Continous Learning}

\end{metasection}

\begin{metasection}{Weakness}

	\cvtags{Introvert} 


\end{metasection}

\end{minipage}}


\end{document}
