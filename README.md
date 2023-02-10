# Bert-Bank-Model

By clicking on the icon, you can use the "bert-bank-model" model over the Hugging Face.

<a href="https://huggingface.co/elifftosunn/Bert-Bank-Model" target="blank"><img align="center" src="https://huggingface.co/landing/assets/transformers-docs/huggingface_logo.svg"></a>


## About the Bert-Bank-Model

It is a Turkish BERT-based model that will analyze people's bank complaints and classify them according to one of eight categories. The classification headings are as follows:

- Diğer
- Hesap İşlemleri
- KKB Skor
- Kargo
- Kart İşlemleri
- Kredi İşlemleri
- Limit 
- Müşteri Temsilcisi


![label_percent](https://user-images.githubusercontent.com/92747017/218093891-7c3ddefc-12e3-4c46-b05a-0113cf720654.png)



246412 thousand complaints were used in model training. The success rates in education are as follows.

|        | Kart İşlemleri | Kredi İşlemleri | Hesap İşlemleri | Kargo | Limit | Müşteri Temsilcisi |  KKB Skor | accuracy |
| ------ | ------  | ------ | ------  | ------ | ------ | ------ | ------ | ------ | 
| Precision | 0.977292 | 0.971119 | 0.985294 | 0.953096 | 0.98616 | 0.989115 | 0.991824 | 0.982336 |
| Recall  | 0.978114 | 0.960714 | 0.985294 | 0.986348 | 0.978590 | 0.982224  | 0.992679 | 0.982336 |
| F1 Score | 0.977703 | 0.965889 | 0.985294 | 0.969437 | 0.983577 |  0.985657  | 0.992251 | 0.982336 | 

## Example

```sh
from transformers import AutoTokenizer, TextClassificationPipeline, TFBertForSequenceClassification

tokenizer = AutoTokenizer.from_pretrained("elifftosunn/Bert-Bank-Model")
model = TFBertForSequenceClassification.from_pretrained("elifftosunn/Bert-Bank-Model", from_pt=True)
pipe = TextClassificationPipeline(model=model, tokenizer=tokenizer)

print(pipe('QNB Finansbank 1.39 oranlı 50.000 TL yeni müşterilere özel ihtiyaç kredisi 1.92 oranında veriyor amaç hesap açtırmak kampanyanın hiçbir gerçekçiliği yoktur. Resmen milletle dalga geçiyorsunuz. Ne demek oluyor bu. 1,39 dan kredi deyip içeriğine girince 2 katına çıkıyor. Böyle saçma bir banka'))

```

## Result

```sh
[{'label': 'Kredi İşlemleri', 'score': 0.9589990377426147}]
```



