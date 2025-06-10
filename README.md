# Cambios-moto
Para llevar el seguimiento de cambios y mantenimiento a la motocicleta o automóvil desde su dispositivo.

Para preguntas comucarse vía WhatsApp al https://wa.me/573025120941

## paso 1

descargar de la playstore PyDroid 3 (pyto en iPhone) y apcete todos los permisos

## paso 2

copiar y pegar el siguiente código Pydroid

```python
mantenimiento_moto = {
# Cambios de Fluidos y Filtros
    "cambio_aceite_motor_km": 3000,
    "cambio_aceite_sintetico_km": 6000,
    "cambio_filtro_aceite_km": 7000,
    "cambio_filtro_aire_km": 8500,
    "cambio_liquido_frenos_km": 18000,
    "cambio_liquido_refrigerante_km": 27000,
# Sistema de Transmisión
    "limpieza_lubricacion_cadena_km": 500,
    "ajuste_tension_cadena_km": 1200,
    "cambio_kit_arrastre_km": 23000,
# Frenos
    "cambio_pastillas_freno_km": 9500,
    "revision_discos_freno_km": 14000,
    "sangrado_liquido_frenos_km": 19500,
# Sistema Eléctrico
    "cambio_bujias_km": 10200,
    "revision_bateria_km": 5400,
    "revision_sistema_electrico_km": 5600,
# Neumáticos y Suspensión
    "revision_presion_neumaticos_km": 1000,
    "cambio_neumaticos_km": 15500,
    "revision_amortiguadores_km": 20500,
# Motor y Partes Mecánicas
    "ajuste_valvulas_km": 15800,
    "cambio_correa_distribucion_km": 42000,
    "limpieza_carburador_km": 10900,
# Revisiones Generales
    "revision_general_km": 5000,
}

def proximos_mantenimientos(kilometraje_actual):
    mantenimientos_proximos = []

    for nombre, intervalo_km in mantenimiento_moto.items():
        # Calcula las próximas 3 repeticiones (para evitar sobrecargar la lista)
        if kilometraje_actual < intervalo_km:
            proximo_km = intervalo_km
        else:
            proximo_km = ((kilometraje_actual // intervalo_km) + 1) * intervalo_km
        for repeticion in range(3):  # Próximas 3 ocurrencias de este mantenimiento
            km = proximo_km + (repeticion * intervalo_km)
            mantenimientos_proximos.append((nombre, km))

    # Ordenar por kilometraje y filtrar únicos (por si hay duplicados cercanos)
    mantenimientos_proximos = sorted(list(set(mantenimientos_proximos)), key=lambda x: x[1])

    # Tomar los 5 más cercanos
    proximos_5 = mantenimientos_proximos[:15]

    # Mostrar resultados
    print(f"\nPróximos 15 mantenimientos (a partir de {kilometraje_actual} km) serán:")
    print("-" * 60)
    for nombre, km in proximos_5:
        nombre_formateado = nombre.replace("_", " ").replace(" km", "").title()
        print(f"{km} km {nombre_formateado:<30} → (faltan {km - kilometraje_actual} km)")
    print("-" * 60)

# Ejemplo de uso
try:
    kilometraje_actual = int(input("Ingrese el kilometraje actual de su vehículo (km): "))
    kilometraje_actual -= 100
    proximos_mantenimientos(kilometraje_actual)
except ValueError:
    print("Error: Ingrese un número válido y no letras")
```

## paso3

Ejecutar el archivo con el círculo amarillo

## paso 4

El programa se verá algo así:

```
Ingrese el kilometraje actual de su vehículo (km):






```
Ingrese el kilometraje que marca su vehículo por ejemplo 8888
```
Ingrese el kilometraje actual de su vehículo (km): 8888

Próximos 15 mantenimientos (a partir de 8788 km):
------------------------------------------------------------
9000 km Revision Presion Neumaticos    → (faltan 212 km)
9000 km Limpieza Lubricacion Cadena    → (faltan 212 km)
9000 km Cambio Aceite Motor            → (faltan 212 km)
9500 km Cambio Pastillas Freno         → (faltan 712 km)
9500 km Limpieza Lubricacion Cadena    → (faltan 712 km)
9600 km Ajuste Tension Cadena          → (faltan 812 km)
10000 km Revision General               → (faltan 1212 km)
10000 km Revision Presion Neumaticos    → (faltan 1212 km)
10000 km Limpieza Lubricacion Cadena    → (faltan 1212 km)
10200 km Cambio Bujias                  → (faltan 1412 km)
10800 km Revision Bateria               → (faltan 2012 km)
10800 km Ajuste Tension Cadena          → (faltan 2012 km)
10900 km Limpieza Carburador            → (faltan 2112 km)
11000 km Revision Presion Neumaticos    → (faltan 2212 km)
11200 km Revision Sistema Electrico     → (faltan 2412 km)
------------------------------------------------------------

[Program finished] 
```
para volver a consultar oprima el icono de flecha izquierda y vuelver a oprima el círculo amarillo
