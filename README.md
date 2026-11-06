# Parole — transcription vidéo locale

## Démarrer gratuitement sur macOS

1. Installe les outils nécessaires :

   ```sh
   brew install ffmpeg whisper.cpp
   ```

2. Télécharge une seule fois le modèle multilingue Whisper `base` (environ 142 Mio) :

   ```sh
   mkdir -p "$HOME/.local/share/parole"
   curl -L "https://huggingface.co/ggerganov/whisper.cpp/resolve/main/ggml-base.bin" -o "$HOME/.local/share/parole/ggml-base.bin"
   ```

3. Dans le Terminal, va dans le dossier `outputs`, puis démarre le site :

   ```sh
   python3 server.py
   ```

4. Ouvre <http://127.0.0.1:8000> et importe une vidéo.

La transcription tourne localement sur le Mac avec Whisper.cpp : aucune clé API ni facture par minute. Le modèle est téléchargé une fois et la vidéo n’est pas envoyée à un service externe. Le modèle `base` utilise environ 388 Mio de mémoire selon le projet Whisper.cpp. Un modèle plus grand peut améliorer le résultat, mais demande plus de mémoire et de temps.

FFmpeg découpe l’audio en blocs et les fichiers temporaires sont supprimés après le traitement. Pour utiliser un autre modèle, indique son chemin dans `WHISPER_MODEL_PATH` avant de démarrer le serveur.
