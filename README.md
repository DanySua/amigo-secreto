# amigo-secreto
import random

def asignar_amigo_secreto(participantes):
    # Mezclar la lista de participantes
    random.shuffle(participantes)
    
    # Asignar amigo secreto
    asignaciones = {}
    for i in range(len(participantes)):
        asignaciones[participantes[i]] = participantes[(i + 1) % len(participantes)]
    
    return asignaciones

def main():
    print("¡Bienvenido al sorteo de Amigo Secreto!")
    
    # Pedir nombres de los participantes
    participantes = []
    while True:
        nombre = input("Ingresa el nombre de un participante (o escribe 'fin' para terminar): ")
        if nombre.lower() == 'fin':
            break
        participantes.append(nombre)
    
    # Verificar que haya suficientes participantes
    if len(participantes) < 2:
        print("Necesitas al menos 2 participantes para realizar el sorteo.")
        return
    
    # Realizar el sorteo
    asignaciones = asignar_amigo_secreto(participantes)
    
    # Mostrar resultados
    print("\n¡El sorteo ha terminado! Aquí están las asignaciones:")
    for persona, amigo in asignaciones.items():
        print(f"{persona} -> {amigo}")

if __name__ == "__main__":
    main()
