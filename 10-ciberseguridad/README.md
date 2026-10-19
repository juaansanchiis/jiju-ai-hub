# 🏴‍☠️ Ciberseguridad y Reverse Engineering (Nivel Hacker)

Plugins de IA para herramientas de análisis de bajo nivel: descompilación, búsqueda de vulnerabilidades, auditorías de seguridad. Para los que les gusta el bajo nivel, la descompilación y buscar vulnerabilidades.

## Tabla de contenidos

- [Ghidra + LLM](ghidra-llm/README.md)
- [PentestGPT](pentestgpt/README.md)

## Herramientas principales

| Herramienta | Tipo | Enlace | Descripción |
| --- | --- | --- | --- |
| Ghidra + LLM (GPT-WPRE / Ghidrathon) | Plugin de reverse engineering | [github.com/NationalSecurityAgency/ghidra](https://github.com/NationalSecurityAgency/ghidra) | Scripts que cogen Assembly descompilado en Ghidra, lo pasan a un LLM local y devuelven C/C++ comentado. |
| PentestGPT | Asistente de pentesting | [github.com/GreyDGL/PentestGPT](https://github.com/GreyDGL/PentestGPT) | Asistente interactivo para la terminal de Linux que guía auditorías de seguridad (Nmap, Metasploit, etc.). |

## Otras herramientas relacionadas

| Herramienta | Tipo | Enlace | Descripción |
| --- | --- | --- | --- |
| Binary Ninja + LLM | Descompilador con IA | [binary.ninja](https://binary.ninja/) | Descompilador comercial con plugins de IA para análisis de binarios. |
| IDA Pro + LLM | Desensamblador con IA | [hex-rays.com](https://hex-rays.com/) | El estándar de la industria; plugins de IA para renombrar funciones y comentar código. |
| Radare2 / Cutter | RE open-source | [rada.re](https://rada.re/) | Framework de reverse engineering open-source con soporte de scripts. |
| angr | Análisis simbólico | [angr.io](https://angr.io/) | Framework de análisis binario simbólico para encontrar vulnerabilidades. |
| Ghidrathon | Python en Ghidra | [github.com/mandiant/Ghidrathon](https://github.com/mandiant/Ghidrathon) | Ejecuta Python 3 en Ghidra para automatizar análisis. |
| GPT-WPRE | Plugin Ghidra+LLM | [github.com/0x6d69636b/GPT-WPRE](https://github.com/0x6d69636b/GPT-WPRE) | Plugin de Ghidra que usa LLMs para renombrar y comentar funciones. |
| ReversingLabs | Análisis de malware | [reversinglabs.com](https://www.reversinglabs.com/) | Plataforma de análisis de malware con IA. |
| VirusTotal | Análisis de archivos | [virustotal.com](https://www.virustotal.com/) | Análisis multi-antivirus con API gratuita. |
| Shodan | Búsqueda de dispositivos | [shodan.io](https://www.shodan.io/) | Buscador de dispositivos conectados a internet. |
| Metasploit | Framework de explotación | [metasploit.com](https://www.metasploit.com/) | Framework estándar para pentesting. |
| Nmap | Escáner de red | [nmap.org](https://nmap.org/) | Escáner de puertos y servicios. |
| Burp Suite | Proxy web | [portswigger.net](https://portswigger.net/burp) | Proxy para testing de seguridad web. |
| OWASP ZAP | Scanner web | [zaproxy.org](https://www.zaproxy.org/) | Scanner de seguridad web open-source. |

## ⚠️ Advertencia ética y legal

- Usa estas herramientas **solo** en sistemas que posees o para los que tienes autorización escrita.
- El pentesting no autorizado es ilegal en la mayoría de jurisdicciones.
- Nunca uses estas herramientas para atacar sistemas de terceros sin permiso.
- Respeta las leyes de tu país (CFAA en EE.UU., Directiva NIS2 en la UE, etc.).

## Buenas prácticas

1. Trabaja siempre en entornos aislados (VMs, contenedores).
2. Documenta cada paso de tu análisis.
3. Usa modelos locales para no enviar binarios a terceros.
4. Combina análisis estático (Ghidra) con dinámico (debugger).
5. Valida los resultados del LLM manualmente (pueden alucinar).
