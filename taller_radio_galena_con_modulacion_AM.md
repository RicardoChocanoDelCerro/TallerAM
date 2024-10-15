
# Taller de Radio Galena

## Introducción Teórica

La **Radio Galena** es uno de los primeros tipos de radios, popular a principios del siglo XX por su simplicidad. Utiliza un detector de cristal (normalmente un diodo de galena) para captar señales de radio AM sin necesidad de una fuente de alimentación externa, aprovechando la energía de la propia señal de radio. Su nombre proviene del mineral de sulfuro de plomo (galena) usado en los primeros detectores.

El principio de funcionamiento se basa en la detección de la señal de radio a través de la rectificación de la onda portadora, lo que permite extraer la señal de audio. Los componentes principales son:
- **Antena**: Captura las ondas de radio.
- **Bobina**: Sintoniza la señal al variar la inductancia.
- **Diodo de Galena**: Actúa como detector, permitiendo el paso de la señal solo en una dirección.
- **Auricular de alta impedancia**: Convierte la señal detectada en sonido.

A diferencia de las radios modernas, las radios de galena no tienen amplificación, por lo que la intensidad de la señal captada depende completamente de la antena y la calidad de la sintonización.

## Materiales y Herramientas

Para construir la **Radio Galena** tal como se muestra en el video, se necesitan los siguientes componentes:

- **Diodo de galena**: Utilizado como el detector principal de la radio.
- **Bobina**: Realizada con cable de cobre esmaltado enrollado en un núcleo no conductor.
- **Condensador variable**: Permite ajustar la sintonización de las señales de radio.
- **Auricular de alta impedancia**: Para la salida de audio.
- **Antena**: Cable largo utilizado para captar las ondas de radio.
- **Tierra**: Un conductor conectado a una toma de tierra para mejorar la recepción.

## Experimentos

### Montaje de la Radio Galena

1. **Construcción de la bobina**: Enrolla el cable de cobre esmaltado sobre un tubo de plástico. La cantidad de vueltas influye en la frecuencia que se puede captar. Cuanto más vueltas, más baja será la frecuencia que la radio puede sintonizar.

2. **Conexión del diodo de galena**: Conecta el diodo a uno de los extremos de la bobina. Este diodo será el encargado de rectificar la señal.

3. **Antena y Tierra**: Conecta un cable largo como antena a uno de los extremos de la bobina y otro a una toma de tierra (como una cañería o un radiador metálico). Esto permitirá captar la señal de radio.

4. **Salida de audio**: Conecta los auriculares de alta impedancia al circuito, entre el diodo y el extremo de la bobina.

5. **Ajuste de sintonización**: Utilizando el condensador variable, sintoniza la radio ajustando la capacidad de la bobina para captar distintas frecuencias.

### Pruebas y Observaciones

- **Captación de la señal**: Al conectar el auricular, se podrá escuchar la señal de la emisora sintonizada. En este caso, al variar la capacidad del condensador, la radio responderá a diferentes estaciones.
  
- **Efecto de la antena**: La calidad y claridad de la señal dependen en gran medida de la longitud y calidad de la antena. Se observa que cuanto más larga es la antena, más estaciones se pueden captar y con mayor claridad.

- **Uso del diodo de galena**: El diodo permite convertir la señal de alta frecuencia en una señal audible. La calidad del cristal de galena o diodo usado influye en la sensibilidad de la radio.

## Demostración en Matlab: Modulación AM

La **modulación de amplitud (AM)** es el proceso mediante el cual la amplitud de una señal portadora se varía en función de una señal de información. En una radio AM, la señal de audio modula una señal portadora de mayor frecuencia, lo que permite transmitir la información a largas distancias.

Aquí se muestra una simulación en **Matlab** para generar una señal modulada en amplitud y luego demodularla:

```matlab
% Parámetros de la simulación
Fs = 10000;          % Frecuencia de muestreo
t = 0:1/Fs:0.1;      % Tiempo de simulación
fc = 500;            % Frecuencia de la portadora (Hz)
fm = 50;             % Frecuencia de la señal moduladora (Hz)
Am = 1;              % Amplitud de la señal moduladora
Ac = 1;              % Amplitud de la señal portadora

% Señal moduladora
m_t = Am*sin(2*pi*fm*t);

% Señal portadora
c_t = Ac*sin(2*pi*fc*t);

% Modulación AM
s_t = (1 + m_t) .* c_t;

% Demodulación AM (Envolvente)
r_t = abs(hilbert(s_t));

% Gráficas
figure;
subplot(3,1,1);
plot(t, m_t);
title('Señal moduladora');
xlabel('Tiempo (s)');
ylabel('Amplitud');

subplot(3,1,2);
plot(t, s_t);
title('Señal modulada (AM)');
xlabel('Tiempo (s)');
ylabel('Amplitud');

subplot(3,1,3);
plot(t, r_t);
title('Señal demodulada (AM)');
xlabel('Tiempo (s)');
ylabel('Amplitud');
```

### Explicación:

1. **Señal moduladora**: Es una señal de baja frecuencia que contiene la información (por ejemplo, el audio que queremos transmitir).
2. **Señal portadora**: Es una señal de alta frecuencia que se utiliza para transportar la señal moduladora.
3. **Señal modulada (AM)**: Es el resultado de la modulación en amplitud, donde la amplitud de la señal portadora varía de acuerdo con la señal moduladora.
4. **Demodulación (Envolvente)**: Utilizando la función `hilbert`, se puede extraer la envolvente de la señal, que es la señal moduladora original.

## Conclusiones

La **Radio Galena** es una excelente demostración de cómo se pueden captar señales de radio sin necesidad de energía externa, mostrando la simplicidad y eficiencia de los primeros sistemas de comunicación. A través de este experimento, se pueden entender conceptos clave como la sintonización, la detección de señales y la importancia de una buena antena para mejorar la recepción.

Además, la simulación en Matlab de la **modulación AM** muestra cómo se puede generar y demodular una señal de radio, lo que permite profundizar en el estudio de las comunicaciones AM.

Si bien la Radio Galena tiene limitaciones en cuanto a sensibilidad y calidad de la señal, es un paso fundamental en la historia de la radio. La experiencia práctica de construirla ofrece una comprensión básica de los principios que gobiernan la transmisión y recepción de señales de radio.
