# project-with-python-about-a-words-to-voice-translator

from gtts import gTTS
import webbrowser
import datetime

# Supported languages
languages = {
    "1": ("English", "en"),
    "2": ("Hindi", "hi"),
    "3": ("French", "fr"),
    "4": ("German", "de"),
    "5": ("Spanish", "es")
}

print("=" * 50)
print("      EchoLang - AI Voice Translator")
print("=" * 50)

print("\nAvailable Languages:")

for key, value in languages.items():
    print(f"{key}. {value[0]}")

choice = input("\nSelect Language Number: ")

if choice not in languages:
    print("Invalid Choice!")

else:
    language_name = languages[choice][0]
    language_code = languages[choice][1]

    print(f"\nSelected Language: {language_name}")

    # User input
    text = input("\nEnter your text: ")

    print("\nGenerating AI Voice...")

    # Text to speech
    tts = gTTS(text=text, lang=language_code)

    # Create unique filename
    filename = "voice_" + datetime.datetime.now().strftime("%H%M%S") + ".mp3"

    # Save audio
    tts.save(filename)

    print("\n================================")
    print("Translation & Voice Generation Complete")
    print("================================")

    print(f"\nLanguage Selected : {language_name}")
    print(f"Audio File Saved  : {filename}")
    print(f"Character Count   : {len(text)}")

    # Save text report
    report = open("report.txt", "w", encoding="utf-8")

    report.write("EchoLang Project Report\n")
    report.write("========================\n\n")
    report.write(f"Language : {language_name}\n")
    report.write(f"Input Text : {text}\n")
    report.write(f"Audio File : {filename}\n")

    report.close()

    print("\nReport saved as report.txt")

    # Open audio automatically
    webbrowser.open(filename)

    print("\nThank you for using EchoLang!")
