#!/bin/bash

# Funzione per verificare dispositivi iPhone collegati
check_devices() {
    echo "Controllo dispositivi collegati..."
    ios_device=$(system_profiler SPUSBDataType | grep -i "iPhone" | wc -l)
    if [[ $ios_device -gt 0 ]]; then
        echo "iPhone rilevato!"
    else
        echo "Nessun iPhone collegato."
    fi
}

# Loop infinito controllabile
run_loop() {
    while true; do
        echo "Esecuzione del ciclo infinito. Premi CTRL+C per fermare."
        sleep 2
    done
}

# Menu interattivo
while true; do
    echo "\nMenu Principale:"
    echo "1) Controlla dispositivi collegati"
    echo "2) Avvia ciclo infinito"
    echo "3) Esci"
    read -rp "Seleziona un'opzione: " choice

    case $choice in
        1)
            check_devices
            ;;
        2)
            echo "Avvio del ciclo infinito..."
            run_loop
            ;;
        3)
            echo "Uscita dal programma."
            exit 0
            ;;
        *)
            echo "Opzione non valida. Riprova."
            ;;
    esac
done
