# Visual Question Answering (VQA)
This project aims to implement a Visual Question Answering (VQA) system using a multimodal architecture. The system takes in an image and a question as inputs, and produces an answer as output. The goal is to use the image to generate the correct answer to the question asked, by using a CNN and an LSTM.

## Baseline DL Approach
The baseline DL approach consisted of a CNN and an LSTM, which produced an accuracy of 35.36%.

## Advanced DL Approach
To improve the performance of the VQA system, we added a stacked attention layer to the architecture, creating the advanced DL approach. This resulted in an accuracy of 54.82%. The advanced DL approach produced visually reasonable and logically sound answers among its top-5 predictions. The stacked attention layers helped in multi-step reasoning and focusing on relevant portions of the image to detect the answer.

## Dataset
The project utilizes the latest version of a standard Visual Question Answering dataset - Visual VQA dataset v2.0. This release consists of 82,783 MS COCO training images, 40,504 MS COCO validation images and 81,434 MS COCO testing images. Along with the images, this release also has 443,757 questions for training, 214,354 questions for validation and 447,793 questions for testing. This dataset comprises of 4,437,570 answers for training and 2,143,540 answers for validation. The questions and answers within the dataset were collected by the authors of the VQA paper using Amazon Mechanical Turk to elicit a more interesting set of questions and answers since the MS COCO images have a lot of diversity and richness.

## Running the code
The code was ran in an AWS EC2 instance (g4dn.12xlarge). For the sake of the project code submission, we have compiled it all in Google Colab files. However, we could not upload all the train, test, validation images due to size and time constraints but we have provided the zip folder.

## To run inference:

Open the Baseline_DL.ipynb or Advanced_DL.ipynb file
Run all the blocks. Please note that the training block will give an error because there are no images loaded. The block still needs to be run to initialize the models.
Run the inference block which follows the training loop
You can change the 'question' variable to a question you'd like to ask.

## Conclusion
This project aimed to implement a Visual Question Answering system using a multimodal architecture. The advanced DL approach, which included a stacked attention layer, outperformed the baseline, producing an accuracy of 54.82%. The stacked attention layers helped in multi-step reasoning and focusing on relevant portions of the image to detect the answer.
