# Visual Question Answering (VQA) using Stacked Attention Networks
![image](https://user-images.githubusercontent.com/38180831/213107520-51c9c570-8be5-4ee1-b874-a0d78856b727.png)

This project aims to implement a Visual Question Answering (VQA) system using a multimodal architecture. The system takes in an image and a question as inputs, and produces an answer as output. The goal is to use the image to generate the correct answer to the question asked, by using a CNN and an LSTM.

## Baseline Deep Learning Approach
In our baseline approach, we implemented a 2-channel vision + language model, which fused embeddings from both these channels via point-wise multiplication. These fused embeddings were then passed through fully-connected layers. To obtain the answer, we generated a probability distribution over the range of
possible answer classes.

![image](https://user-images.githubusercontent.com/38180831/213108042-741bfe93-63de-4b9b-a958-0e2e3c489e74.png)


The different components of architecture are outlined as follows:

1. Image Channel - This channel provides l2 normalized activations from the last hidden layer of VGGNet for the images. The image embeddings are transformed to 1024-dimensions by using a fully connected layer and tanh non-linearity.

2. Question Channel - For the embedding of the question, an LSTM with 2 hidden layers is used. The 2048-dimension embedding obtained from the
LSTM is a concatenation of the last cell state and last hidden state repre- sentation. To transform the 2048-dimension encoding to 1024-dimensions, we used a fully connected layer and tanh non-linearity.

3. Multi-Layer Perceptron - The 1024-dimension image and question embed- dings are fused together via point-wise multiplication to obtain a single
embedding. This fused embedding is then passed through fully-connected layers. The Multi-Layer Perceptron unit consists of 2 linear layers, each with 1000 hidden units. Each of the hidden layers was also followed by a dropout layer (set to 0.5) and tanh nonlinearity. The MLP unit is then followed by a softmax layer to obtain a probabiltiy distribution over the 1000 possible words from the answer vocabulary.

## Advanced Deep Learning Approach

![image](https://user-images.githubusercontent.com/38180831/213108602-17595b09-fc7d-44ba-a687-faaf6943a1ed.png)

To improve the performance of the VQA system, we added a stacked attention layer to the architecture, creating the advanced DL approach. This resulted in an accuracy of 54.82%. The advanced DL approach produced visually reasonable and logically sound answers among its top-5 predictions. The stacked attention layers helped in multi-step reasoning and focusing on relevant portions of the image to detect the answer.

Visualization of Attention for First and Second Layers:
![image](https://user-images.githubusercontent.com/38180831/213108702-21243112-4cf6-4475-b30a-55baa16e965e.png)

## Dataset
The project utilizes the latest version of a standard Visual Question Answering dataset - Visual VQA dataset v2.0. This release consists of 82,783 MS COCO training images, 40,504 MS COCO validation images and 81,434 MS COCO testing images. Along with the images, this release also has 443,757 questions for training, 214,354 questions for validation and 447,793 questions for testing. This dataset comprises of 4,437,570 answers for training and 2,143,540 answers for validation. 

Download and unzip the dataset from official url of VQA: https://visualqa.org/download.html.

## Running the code
We have compiler the training and testing code in iPython Notebook to simplify the setup process

1. Open the `Baseline_DL.ipynb` or `Advanced_DL.ipynb` file
2. Run all the blocks. Please note that the training block will give an error because there are no images loaded. The block still needs to be run to initialize the models.
3. Run the inference block which follows the training loop
4. You can change the 'question' variable to a question you'd like to ask.

## Results
This project aimed to implement a Visual Question Answering system using a multimodal architecture. The advanced DL approach, which included a stacked attention layer, outperformed the baseline, producing an accuracy of 54.82%. The stacked attention layers helped in multi-step reasoning and focusing on relevant portions of the image to detect the answer.

Accuracies of the three approaches on different types of questions:
![image](https://user-images.githubusercontent.com/38180831/213110943-41998ffc-811c-4a0b-9625-c4fe727aa880.png)
![image](https://user-images.githubusercontent.com/38180831/213111076-2cc1ce96-6bfd-4ed7-8ebd-e2c7b3034cf5.png)
![image](https://user-images.githubusercontent.com/38180831/213111127-0a544e38-71b2-4a1b-be89-061bb7cde1a0.png)
![image](https://user-images.githubusercontent.com/38180831/213111162-b7fb9ef1-cf8b-4eec-bdf9-82dda941fd4e.png)


## References
* Paper implementation
  + Keywords: Visual Question Answering ; Simple Attention; Stacked Attention; Top-Down Attention;
    
* Baseline Model
  + Github: https://github.com/tbmoon/basic_vqa

