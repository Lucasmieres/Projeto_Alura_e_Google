{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "provenance": [],
      "authorship_tag": "ABX9TyMT/oiUFpMuXY3KBsEQmhmU",
      "include_colab_link": true
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/Lucasmieres/Projeto_Alura_e_Google/blob/main/README.md\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "Instalando o SDK do google"
      ],
      "metadata": {
        "id": "voFFadqndH_-"
      }
    },
    {
      "cell_type": "code",
      "execution_count": 1,
      "metadata": {
        "id": "scN8VJckdHCJ"
      },
      "outputs": [],
      "source": [
        "!pip install -q -U google-generativeai"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "#Configurações iniciais"
      ],
      "metadata": {
        "id": "GMYypKRldWMX"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "#modelo\n",
        "import google.generativeai as genai\n",
        "from google.colab import userdata\n",
        "api_key = usardate.get(\"secret_key\")\n",
        "\n",
        "genai.configure(api_key=api_key)"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 211
        },
        "id": "aDtVvIACdXDE",
        "outputId": "88ac0f49-d144-4bf9-d36e-1c9a12d37c5b"
      },
      "execution_count": 44,
      "outputs": [
        {
          "output_type": "error",
          "ename": "NameError",
          "evalue": "name 'usardate' is not defined",
          "traceback": [
            "\u001b[0;31m---------------------------------------------------------------------------\u001b[0m",
            "\u001b[0;31mNameError\u001b[0m                                 Traceback (most recent call last)",
            "\u001b[0;32m<ipython-input-44-0976393a7833>\u001b[0m in \u001b[0;36m<cell line: 4>\u001b[0;34m()\u001b[0m\n\u001b[1;32m      2\u001b[0m \u001b[0;32mimport\u001b[0m \u001b[0mgoogle\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mgenerativeai\u001b[0m \u001b[0;32mas\u001b[0m \u001b[0mgenai\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m      3\u001b[0m \u001b[0;32mfrom\u001b[0m \u001b[0mgoogle\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mcolab\u001b[0m \u001b[0;32mimport\u001b[0m \u001b[0muserdata\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m----> 4\u001b[0;31m \u001b[0mapi_key\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0musardate\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mget\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0;34m\"secret_key\"\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m      5\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m      6\u001b[0m \u001b[0mgenai\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mconfigure\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mapi_key\u001b[0m\u001b[0;34m=\u001b[0m\u001b[0mapi_key\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
            "\u001b[0;31mNameError\u001b[0m: name 'usardate' is not defined"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [],
      "metadata": {
        "id": "fMvz1Yw_2qIY"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Listando os modelos disponiveis"
      ],
      "metadata": {
        "id": "E7ciYD5VdZg_"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "for m in genai.list_models():\n",
        "  if 'generateContent' in m.supported_generation_methods:\n",
        "    print(m.name)"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 139
        },
        "id": "isRQGgq5eWX1",
        "outputId": "c073a84c-215e-4275-cf8c-7b8bad8d7bc8"
      },
      "execution_count": 8,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "models/gemini-1.0-pro\n",
            "models/gemini-1.0-pro-001\n",
            "models/gemini-1.0-pro-latest\n",
            "models/gemini-1.0-pro-vision-latest\n",
            "models/gemini-1.5-pro-latest\n",
            "models/gemini-pro\n",
            "models/gemini-pro-vision\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "generation_config = {\n",
        "  \"candidate_count\": 1,\n",
        "  \"temperature\": 0.5,\n",
        "}\n"
      ],
      "metadata": {
        "id": "1KkiQFl-gUYv"
      },
      "execution_count": 27,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "configuracao de moderacao do chat"
      ],
      "metadata": {
        "id": "JdJIE_rtiHsf"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "safety_settings={\n",
        "    'HATE': 'BLOCK_NONE',\n",
        "    'HARASSMENT': 'BLOCK_NONE',\n",
        "    'SEXUAL' : 'BLOCK_NONE',\n",
        "    'DANGEROUS' : 'BLOCK_NONE'\n",
        "    }"
      ],
      "metadata": {
        "id": "f7KqT793hECG"
      },
      "execution_count": 30,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Iniciando o modelo"
      ],
      "metadata": {
        "id": "_Wflm5y1j6bz"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "model = genai.GenerativeModel(model_name='gemini-1.0-pro',\n",
        "                                  generation_config=generation_config,\n",
        "                                  safety_settings=safety_settings,)"
      ],
      "metadata": {
        "id": "RWxVz1lakAHE"
      },
      "execution_count": 31,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "response = model.generate_content(\"Que empresa criou o modelo de IA Gemini?\")\n",
        "response.text"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 35
        },
        "id": "oky8vXvJq0Dk",
        "outputId": "9ee82a17-8ea9-4405-a9bf-774d654e9a42"
      },
      "execution_count": 35,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "'Google'"
            ],
            "application/vnd.google.colaboratory.intrinsic+json": {
              "type": "string"
            }
          },
          "metadata": {},
          "execution_count": 35
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "chat = model.start_chat(history=[])\n",
        "\n",
        "prompt = input('Esperando prompt: ')\n",
        "\n",
        "while prompt != \"fim\":\n",
        "  response = chat.send_message(prompt)\n",
        "  print(\"Resposta:\", response.text, '\\n\\n')\n",
        "  prompt = input('Esperando prompt: ')"
      ],
      "metadata": {
        "id": "xPpeXNyVrgE-"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "#Melhorando a visualização\n",
        "#Código disponível em https://ai.google.dev/tutorials/python_quickstart#import_packages\n",
        "import textwrap\n",
        "from IPython.display import display\n",
        "from IPython.display import Markdown\n",
        "\n",
        "def to_markdown(text):\n",
        "  text = text.replace('•', '  *')\n",
        "  return Markdown(textwrap.indent(text, '> ', predicate=lambda _: True))\n",
        "\n",
        "#Imprimindo o histórico\n",
        "for message in chat.history:\n",
        "  display(to_markdown(f'**{message.role}**: {message.parts[0].text}'))\n",
        "  print('-------------------------------------------')"
      ],
      "metadata": {
        "id": "88t87WAgtR3k"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "chat.history"
      ],
      "metadata": {
        "id": "xaxRAtAztamB"
      },
      "execution_count": null,
      "outputs": []
    }
  ]
}