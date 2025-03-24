# Sistema RAG híbrido con Topic Modeling
El codigo se encuentra en un notebook donde la data se extrae de un dataset de Kaggle.

Para poder ejecutar el codigo basta con abrir el enlace en algun editor de codigo que permita ejecutar python notebooks e instalar las siguientes dependencias
```
! pip install sentence-transformers
! pip install hdbscan umap-learn
! pip install keybert
```
Ademas, es necesario descargar el dataset de [arXiv Scientific Research Papers Dataset](https://www.kaggle.com/datasets/sumitm004/arxiv-scientific-research-papers-dataset) de Kaggle y depositarlo en alguna carpeta al que el notebook pueda acceder.

Luego, cambiar la ubicación de la siguiente linea de codigo, ubicada en la seccion de `Document loading`

```
df = pd.read_csv('/kaggle/input/arxiv-scientific-research-papers-dataset/arXiv_scientific dataset.csv')
```

Finalmente, el notebook almacena los embeddings, modelos y keywords para poder se utilizados en el futuro, por lo que también es necesario cambiar las siguientes rutas

En la seccion `Embeddings`

- `if os.path.isfile('/kaggle/working/document_embeddings.npy'):`
- `document_embeddings = np.load('/kaggle/working/document_embeddings.npy', allow_pickle=True)`

Se recomienda ejecutar el sistema por primera vez con una GPU para acelerar el procesos de generación de embeddings. Se procesan 2.7k documentos, usando GPU todo el notebook tarda poco más de 4 minutos.
