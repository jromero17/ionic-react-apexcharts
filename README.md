<p align="center"><img src="https://apexcharts.com/media/react-apexcharts.png"></p>
<div align="center">
    <p>
        <a href="https://imunes.net"><img src="https://github.com/jromero17/logos/blob/IMUNES-Multi-Idiomas/ionic-react-capacitor.png?raw=true" title="ionic react capacitor https://apexcharts.com/javascript-chart-demos/column-charts/" alt="Apexcharts Website" width="250" /></a>
    </p> 
</div>

<p align="center">
  <a href="https://github.com/apexcharts/react-apexcharts/blob/master/LICENSE"><img src="https://img.shields.io/badge/License-MIT-brightgreen.svg" alt="License"></a>
  <a href="https://travis-ci.com/apexcharts/react-apexcharts"><img src="https://api.travis-ci.com/apexcharts/react-apexcharts.svg?branch=master" alt="build" /></a>
  <a href="https://www.npmjs.com/package/react-apexcharts"><img src="https://img.shields.io/npm/v/react-apexcharts.svg" alt="ver"></a>
</p>

<p align="center">
  <a href="https://twitter.com/intent/tweet?text=React-ApexCharts%20A%20React.js%20Chart%20library%20built%20on%20ApexCharts.js&url=https://www.apexcharts.com&hashtags=javascript,charts,react.js,react,apexcharts"><img src="https://img.shields.io/twitter/url/http/shields.io.svg?style=social"> </a>
</p>

<p align="center">React.js wrapper for <a href="https://github.com/apexcharts/apexcharts.js">ApexCharts</a> to build interactive visualizations in react.</p>

<p align="center"><a href="https://apexcharts.com/react-chart-demos/"><img src="https://apexcharts.com/media/apexcharts-banner.png"></a></p>


## Download and Installation

##### Installing via npm

```bash
npm install react-apexcharts apexcharts
```

## Usage

```js
import Chart from 'react-apexcharts';

o

import ReactApexChart from 'react-apexcharts';

```
Vamos a establecer dos formatos estándar para usar react-apexcharts con Ionic React, uno para cuando la gráfica está directamente en una página (como un Tab o Home) y otro para cuando se usa un contenedor.

Formato 1: Gráfica Directamente en una Página (Tab o Home)

Este formato es ideal cuando la gráfica es el elemento principal de la página y no necesita estar dentro de un contenedor separado.

To create a basic bar chart with minimal configuration, write as follows:

Este formato es ideal cuando la gráfica es el elemento principal de la página y no necesita estar dentro de un contenedor separado.

```TypeScript HomePage.tsx
import React, { useState, useEffect } from 'react';
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar } from '@ionic/react';
import Chart from 'react-apexcharts';

interface HomePageProps {}

const HomePage: React.FC<HomePageProps> = () => {
  const [isClient, setIsClient] = useState(false);
  const [options, setOptions] = useState({
    chart: {
      id: 'apexchart-home',
    },
    xaxis: {
      categories: [1991, 1992, 1993, 1994, 1995, 1996, 1997, 1998, 1999],
    },
  });
  const [series, setSeries] = useState([
    {
      name: 'series-1',
      data: [30, 40, 35, 50, 49, 60, 70, 91, 125],
    },
  ]);

  useEffect(() => {
    setIsClient(true);
  }, []);

  return (
    <IonPage>
      <IonHeader>
        <IonToolbar>
          <IonTitle>Home</IonTitle>
        </IonToolbar>
      </IonHeader>
      <IonContent>
        {isClient && (
          <div className="chart-container">
            <Chart options={options} series={series} type="bar" width="100%" height={320} />
          </div>
        )}
      </IonContent>
    </IonPage>
  );
};

export default HomePage;
```
Explicación:

- Componente Funcional: Se utiliza un componente funcional con Hooks para el estado.
- Estado con useState: Se utilizan useState para manejar las opciones del gráfico (options) y los datos de la serie (series).
- Verificación del Lado del Cliente: Se utiliza la técnica de verificación del lado del cliente con useState e useEffect para evitar problemas de renderizado en el servidor.
- Componentes de Ionic React: Se utilizan los componentes de Ionic React IonPage, IonHeader, IonToolbar y IonContent para estructurar la página.
- Renderizado Condicional: El componente Chart solo se renderiza si isClient es true.
- Ancho del grafico: El atributo width="100%" en el componente Chart establece el ancho del grafico al 100%.
- Estilos CSS (Opcional): Se puede agregar un contenedor CSS (chart-container) para controlar el layout del gráfico dentro del IonContent.

Formato 2: Gráfica en un Contenedor (Componente Separado)

Este formato es ideal cuando quieres reutilizar la gráfica en diferentes partes de tu aplicación o cuando quieres mantener la lógica de la gráfica 
separada de la lógica de la página.

```TypeScript GraficContainer.tsx
import React, { useState, useEffect } from 'react';
import Chart from 'react-apexcharts';

interface ContainerProps {}

const GraficContainer: React.FC<ContainerProps> = () => {
  const [isClient, setIsClient] = useState(false);
  const [options, setOptions] = useState({
    chart: {
      id: 'apexchart-container',
    },
    xaxis: {
      categories: [1991, 1992, 1993, 1994, 1995, 1996, 1997, 1998, 1999],
    },
  });
  const [series, setSeries] = useState([
    {
      name: 'series-1',
      data: [30, 40, 35, 50, 49, 60, 70, 91, 125],
    },
  ]);

  useEffect(() => {
    setIsClient(true);
  }, []);

  return (
    <>
      {isClient && (
        <div className="chart-container">
            <Chart
                options={options}
                series={series}
                type="bar"
                width="100%"
                height={320}
            />
        </div>
      )}
    </>
  );
};

export default GraficContainer;
```
Explicación:

- Componente Funcional: Se utiliza un componente funcional con Hooks para el estado.
- Estado con useState: Se utilizan useState para manejar las opciones del gráfico (options) y los datos de la serie (series).
- Verificación del Lado del Cliente: Se utiliza la técnica de verificación del lado del cliente con useState e useEffect para evitar problemas de renderizado en el servidor.
- Renderizado Condicional: El componente Chart solo se renderiza si isClient es true.
- Ancho del grafico: El atributo width="100%" en el componente Chart establece el ancho del grafico al 100%.
- Estilos CSS (Requerido): Se requiere un contenedor CSS (chart-container) para controlar el layout del gráfico dentro del contenedor.

Cómo Utilizarlo en una Página (Tab o Home):

```TypeScript HomePage.tsx
import React from 'react';
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar } from '@ionic/react';
import GraficContainer from '../components/GraficContainer'; // Ajusta la ruta

const HomePage: React.FC = () => {
  return (
    <IonPage>
      <IonHeader>
        <IonToolbar>
          <IonTitle>Home</IonTitle>
        </IonToolbar>
      </IonHeader>
      <IonContent>
        <GraficContainer />
      </IonContent>
    </IonPage>
  );
};

export default HomePage;
```
Estilos CSS (Ejemplo):

```Estilos file.css
/* En un archivo CSS (por ejemplo, GraficContainer.css) */
.chart-container {
  width: 100%;
  max-width: 600px; /* Ajusta el ancho máximo según tus necesidades */
  margin: 0 auto; /* Centrar el contenedor */
}
```
##Resumen:

- Gráfica Directamente en una Página: Utiliza el formato 1 cuando la gráfica es el elemento principal de la página y no necesitas un contenedor separado.
- Gráfica en un Contenedor: Utiliza el formato 2 cuando quieres reutilizar la gráfica en diferentes partes de tu aplicación o cuando quieres mantener la lógica de la gráfica separada de la lógica de la página.

Estos formatos deberían proporcionar una base sólida para trabajar con react-apexcharts en tus proyectos de Ionic React. Recuerda ajustar los estilos CSS según tus necesidades específicas.

This will render the following chart
<p align="center"><a href="https://apexcharts.com/javascript-chart-demos/column-charts/"><img src="https://apexcharts.com/media/first-bar-chart.svg"></a></p>

### How do I update the chart?
Simple! Just change the `series` or any `option` and it will automatically re-render the chart.
<p align="center"><a href="https://codesandbox.io/s/mzzq3yqjqj"><img src="https://apexcharts.com/media/react-chart-updation.gif"></a></p>

View this example on <a href="https://codesandbox.io/s/mzzq3yqjqj">codesandbox</a>


**Important:** While updating the options, make sure to update the outermost property even when you need to update the nested property.

✅ Do this
```javascript
this.setState({
  options: {
    ...this.state.options,
    xaxis: {
      ...this.state.options.xaxis,
      categories: ['X1', 'X2', 'X3']
    }
  }
})
```

❌ Not this
```javascript
this.setState({
  options.xaxis.categories: ['X1', 'X2', 'X3']
})
```


## Props


| Prop        | Type           | Description  |
| ------------- |-------------| -----|
| **series** | `Array` | The series is a set of data. To know more about the format of the data, checkout [Series docs](https://apexcharts.com/docs/series/) on the website. |
| **type** | `String`  | `line`, `area`, `bar`, `pie`, `donut`, `scatter`, `bubble`, `heatmap`, `radialBar` |
| **width** | `Number or String`  | Possible values for width can be `100%`, `400px` or `400` (by default is `100%`) |
| **height** | `Number or String` | Possible values for height can be `100%`, `300px` or `300` (by default is `auto`) |
| **options** | `Object` | The configuration object, see options on [API (Reference)](https://apexcharts.com/docs/options/chart/type/) |

## How to call methods of ApexCharts programmatically?
Sometimes, you may want to call other methods of the core ApexCharts library, and you can do so on `ApexCharts` global variable directly

Example
```js
ApexCharts.exec('reactchart-example', 'updateSeries', [{
  data: [40, 55, 65, 11, 23, 44, 54, 33]
}])
```
More info on the `.exec()` method can be found <a href="https://apexcharts.com/docs/methods/#exec">here</a>

All other methods of ApexCharts can be called this way

## What's included

The repository includes the following files and directories.

```
react-apexcharts/
├── dist/
│   ├── react-apexcharts.min.js
│   └── react-apexcharts.js
└── example/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── README.md
└── src/
    └── react-apexcharts.jsx
```

## Development

#### Install dependencies

```bash
npm install
```

## Running the example

Basic example including update is included to show how to get started using ApexCharts with React easily.

To run the examples,
```bash
cd example
npm install
npm run start
```

#### Bundling

##### To build for Development

```bash
npm run dev-build
```

##### To build for Production

```bash
npm run build
```

## License

React-ApexCharts is released under MIT license. You are free to use, modify and distribute this software, as long as the copyright header is left intact.
