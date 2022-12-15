# Sunbird AI huggingface-models-tutorial
This tutorial shows how to use the Sunbird AI models deployed on hugging face via the inference API.

## Create a HuggingFace account.
To get access to an API token, you'll need a HuggingFace account. Sign up here: https://huggingface.co/join

## Get your API token
Once, you have an account, go to the tokens page and create a new token: https://huggingface.co/settings/tokens.

![hf-tokens](https://user-images.githubusercontent.com/26762336/207887258-48e0c8eb-2a5d-4ed2-bf6b-1636744eee7d.png)

## Make requests to the model.
To use the model, you can go to the model page: for example, to access the Sunbird English-Multiple Model:
- go to https://huggingface.co/Sunbird/sunbird-en-mul
- click the `Deploy` button.
- Choose `Inference API`.
- You'll find example code in `Python`, `Javascript` and `cURL`, which you can use to make requests to the models.
- Click `Show API token` to see your Authorization token.
![hf-code](https://user-images.githubusercontent.com/26762336/207889883-596e4d90-42fb-4c74-9d2b-7fbb38dca7b9.png)


## Possible issues
Some possible issues you could run into are:
- Model loading error:
```
{
    "error": "Model Sunbird/sunbird-mul-en is currently loading",
    "estimated_time": 20.0
}
```
This means that the model is still loading, and you'll have to try the request again in 20 seconds.

- Number of characters exceeded. The total number of characters in the free tier is 30,000.

## Using the translation models
There are two translation models:
- Multiple to English model (https://huggingface.co/Sunbird/sunbird-mul-en): Translates from multiple languages (currently 5) to English.
- English to Multiple model (https://huggingface.co/Sunbird/sunbird-en-mul): Translates from English to multiple languages.

The `Multiple to English` following input json format (where `text` is the sentence you want to translate):
```
{
    "inputs": "{text}"
}
```

For the `English to Multiple` model, you need to prepend the `text` with a language code specifying the language to which you want to translate. i.e
```
{
    "inputs": ">>lug<<How are you?"
}
```

In this example, `>>lug<<` means Luganda. The table below shows the language codes for all the supported languages:

|Language|Code|
|--------|----|
|Acholi|ach|
|Ateso|teo|
|Luganda|lug|
|Lugbara|lgg|
|Runyankole|nyn|

The output for both models is in the following format:
```
[
    {
        "generated_text": "Oli otya?"
    }
]
```

## Example request in Postman

![translate-postman](https://user-images.githubusercontent.com/26762336/207892984-c76b8bf4-4711-473c-84d2-2ef45326c6b1.png)




