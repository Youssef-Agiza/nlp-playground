# Info about the models

## BloomForCausalLM
- supports generate method
## BloomForQuestionAnswering
- dosent support generate method
# Running the model


if the model supports generate method:
```py
model.generate(inputs["input_ids"],
                       max_length=result_length, 
                       num_beams=2, 
                       no_repeat_ngram_size=2,
                       early_stopping=True)
```

if the model supports forward method:
```py
model(inputs["input_ids"], 
              attention_mask=inputs["attention_mask"], 
              max_length=result_length, 
              num_beams=2, 
              no_repeat_ngram_size=2,
              early_stopping=True)
```

# Printing the output

if the model supports generate method:
```py
print(tokenizer.decode(outputs[0], skip_special_tokens=True))
```

if the model supports forward method:
```py
print(tokenizer.decode(outputs[0].argmax(dim=-1), skip_special_tokens=True)) ## argmax is used to get the most probable token
```