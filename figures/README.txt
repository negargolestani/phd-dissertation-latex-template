Put your figure files here (PDF, PNG, JPG, EPS).
Reference them in the text with, e.g.:

\begin{figure}[H]
    \centering
    \includegraphics[width=0.8\textwidth]{my_figure.png}
    \caption{Your caption text.}
    \label{fig:my_figure}
\end{figure}

The preamble already sets \graphicspath{{./figures/}}, so you can
use just the filename (no "figures/" prefix) in \includegraphics.
