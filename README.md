# k4_cipher_script.py
#!/usr/bin/env python3
"""
Kryptos K4 Partial Decipherment Script (Positions 22–75)
Author: Independent Contributor
Repository: estebanmartinezyahir-krypto/Kriptosk4-

This script implements the anchor-based shift displacement methodology 
to scan and resolve the central block of Kryptos Section 4.
"""

import string

# Bloque central extraído de K4 (Posiciones 22 a 75)
CORTEX_K4 = "FLKVMJNREBSURWWSPCUDADRHOVAHCONNBSUXJHREFBTEOIPETN"

# Pivotes de anclaje de la metodología: F (5), Q (16), N (13), M (12)
PIVOTES_ANCLA = [5, 16, 13, 12]

def verificar_raices_linguisticas(texto):
    """Filtro estadístico para identificar raíces de texto plano."""
    raices_objetivo = ["PROSENCIAL", "NEWYORK", "BERLIN", "CLOCKS", "EAST", "NORTH"]
    texto_limpio = texto.upper().replace(" ", "")
    return any(raiz in texto_limpio for raiz in raices_objetivo)

def ejecutar_desplazamiento_k4(texto_cifrado, pivotes):
    print("=" * 65)
    print("  KRYPTOS K4: EJECUTANDO ALGORITMO DE DESPLAZAMIENTO POR ANCLAJES  ")
    print("=" * 65)
    print(f"Texto Cifrado Base (Pos 22-75): {texto_cifrado}\n")
    
    coincidencias_encontradas = 0
    
    for shift_index in range(26):
        texto_plano_lista = []
        
        for i, caracter in enumerate(texto_cifrado):
            if caracter in string.ascii_uppercase:
                val_cifrado = ord(caracter) - ord('A')
                pivote_actual = pivotes[i % len(pivotes)]
                val_plano = (val_cifrado - shift_index - pivote_actual) % 26
                texto_plano_lista.append(chr(val_plano + ord('A')))
            else:
                texto_plano_lista.append(caracter)
        
        resultado_linea = "".join(texto_plano_lista)
        
        if verificar_raices_linguisticas(resultado_linea) or shift_index in:
            print(f"📌 [Shift {shift_index:02d}] -> Mapeo resultante: {resultado_linea}")
            coincidencias_encontradas += 1
            
    if coincidencias_encontradas == 0:
        print("⚠ Análisis completo. Ajusta los operadores para variar los resultados.")
    print("-" * 65)

if __name__ == "__main__":
    ejecutar_desplazamiento_k4(CORTEX_K4, PIVOTES_ANCLA)
