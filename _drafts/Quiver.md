---
title: "Quiver test"
date: 2022-3-1
---
Testing including Quiver diagrams.

<iframe class="quiver-embed" src="https://q.uiver.app/?q=WzAsNCxbMCwwLCJcXGJ1bGxldCJdLFsyLDIsIlxcYnVsbGV0Il0sWzQsMCwiXFxidWxsZXQiXSxbNiwyLCJcXGJ1bGxldCJdLFswLDEsIkwiLDJdLFswLDIsIlQiXSxbMiwzLCJSIl0sWzEsMywiQiIsMl0sWzEsMiwiXFxtYXRocm17TGFufV9MKFQpIiwwLHsib2Zmc2V0IjotMiwic3R5bGUiOnsiYm9keSI6eyJuYW1lIjoic3F1aWdnbHkifX19XSxbMSwyLCJcXG1hdGhybXtSaWZ0fV9SKEIpIiwyLHsib2Zmc2V0IjoyLCJzdHlsZSI6eyJib2R5Ijp7Im5hbWUiOiJzcXVpZ2dseSJ9fX1dLFs1LDEsIiIsMCx7InNob3J0ZW4iOnsic291cmNlIjoyMH19XSxbMiw3LCIiLDAseyJzaG9ydGVuIjp7InRhcmdldCI6MjB9fV1d&embed" width="944" height="432" style="border-radius: 8px; border: none;"></iframe>
{% comment %}
\[\begin{tikzcd}
  \bullet &&&& \bullet \\
  \\
  && \bullet &&&& \bullet
  \arrow["L"', from=1-1, to=3-3]
  \arrow[""{name=0, anchor=center, inner sep=0}, "T", from=1-1, to=1-5]
  \arrow["R", from=1-5, to=3-7]
  \arrow[""{name=1, anchor=center, inner sep=0}, "B"', from=3-3, to=3-7]
  \arrow["{\mathrm{Lan}_L(T)}", shift left=2, squiggly, from=3-3, to=1-5]
  \arrow["{\mathrm{Rift}_R(B)}"', shift right=2, squiggly, from=3-3, to=1-5]
  \arrow[shorten <=7pt, Rightarrow, from=0, to=3-3]
  \arrow[shorten >=7pt, Rightarrow, from=1-5, to=1]
\end{tikzcd}\]
{% endcomment %}