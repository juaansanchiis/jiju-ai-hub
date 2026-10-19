# 🧠 GraphRAG (El RAG con esteroides)

El RAG tradicional (meter PDFs a una base de datos vectorial) ya es aburrido. Lo que se lleva ahora es el RAG con Grafos de Conocimiento: extrae entidades de tus documentos y crea un mapa mental gigante (un grafo). En lugar de buscar "palabras similares", el LLM razona sobre las conexiones.

## Tabla de contenidos

- [Microsoft GraphRAG](microsoft-graphrag/README.md)
- [LightRAG](lightrag/README.md)

## Herramientas principales

| Herramienta | Tipo | Enlace | Descripción |
| --- | --- | --- | --- |
| Microsoft GraphRAG | Framework de RAG con grafos | [github.com/microsoft/graphrag](https://github.com/microsoft/graphrag) | Extrae entidades y crea un grafo de conocimiento; el LLM razona sobre conexiones. Ideal para apuntes de carrera. |
| LightRAG | RAG con grafos optimizado | [github.com/HKUDS/LightRAG](https://github.com/HKUDS/LightRAG) | Versión súper optimizada y rápida de GraphRAG, corre en local sin gastar muchos tokens. |

## Otras herramientas relacionadas

| Herramienta | Tipo | Enlace | Descripción |
| --- | --- | --- | --- |
| Neo4j | Base de datos de grafos | [neo4j.com](https://neo4j.com/) | La BD de grafos más popular; integra con LLMs vía LangChain. |
| LlamaIndex | Framework RAG | [llamaindex.ai](https://www.llamaindex.ai/) | Soporta GraphRAG y múltiples estrategias de indexación. |
| LangChain | Framework de agentes | [langchain.com](https://www.langchain.com/) | Integración con grafos de conocimiento y RAG. |
| Graphiti (Zep) | Memoria con grafos para agentes | [github.com/getzep/graphiti](https://github.com/getzep/graphiti) | Memoria temporal con grafos de conocimiento para agentes. |
| Mem0 | Memoria para agentes | [github.com/mem0ai/mem0](https://github.com/mem0ai/mem0) | Capa de memoria (incluye grafos) para agentes de IA. |
| Kuzu | BD de grafos embebida | [kuzudb.com](https://kuzudb.com/) | Base de datos de grafos embebida, ideal para apps locales. |
| NetworkX | Grafos en Python | [networkx.org](https://networkx.org/) | Librería estándar para manipular grafos en Python. |
| ChromaDB | BD vectorial | [trychroma.com](https://www.trychroma.com/) | BD vectorial ligera para RAG tradicional. |
| Qdrant | BD vectorial | [qdrant.tech](https://qdrant.tech/) | BD vectorial de alto rendimiento con tier gratuito. |
| Weaviate | BD vectorial | [weaviate.io](https://weaviate.io/) | BD vectorial con soporte de grafos y módulos de IA. |

## RAG tradicional vs GraphRAG

| Aspecto | RAG tradicional | GraphRAG |
| --- | --- | --- |
| Búsqueda | Similitud vectorial | Conexiones en grafo |
| Contexto | Chunks aislados | Relaciones entre entidades |
| Razonamiento | Limitado | Multi-hop reasoning |
| Coste de tokens | Bajo | Alto (indexación) |
| Ideal para | FAQs, docs simples | Apuntes, papers, código |

## Buenas prácticas

1. Usa GraphRAG para corpus con muchas relaciones (apuntes, papers, código).
2. Usa RAG tradicional para FAQs y documentación simple.
3. Combina ambos: vectorial para recall, grafo para reasoning.
4. Limita el tamaño del grafo para controlar costes de indexación.
5. Actualiza el grafo incrementalmente cuando añadas documentos.
