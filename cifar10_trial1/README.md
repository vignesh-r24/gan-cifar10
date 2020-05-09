### Trial 1

#### Model Architecure
1. Discriminator:
   1. Input dimension: (32,32,3)
   1. 2 2D Convolutional layers - [ filters: 128x(3,3), stride=(2,2), padding='same' ]
   1. Each Convolutional layer is followed by BatchNormalization and LeakyReLU(alpha=0.2)
   1. The activations are passed through a Flatten() layer
   1. The ouput layer is a Dense layer with 1 unit (to predict real / fake), and sigmoid activation
   1. Loss: binary_crossentropy
   1. Optimizer: Adam(lr=0.0002, beta_1=0.5)
   1. Output dimension: (1,1)


2. Generator:
   1. Input dimension: 100 (latent input dimension)
   2. First hidden layer: (128x8x8) nodes
   3. Followed by BatchNormalization and LeakyReLU(alpha=0.2)
   4. The output is reshaped to (8,8,128)
   5. 2 2D Transpose Convolutional layers - [ filters: 128x(4,4), stride=(2,2), padding='same' ]
   6. Each Transpose Convolutional layer is followed by BatchNormalization and LeakyReLU(alpha=0.2)
   7. The output layer is a 2D Convolutional layer - [ filters: 3x(5,5), padding='same', activation='sigmoid' ]
   8. Output dimension: (32,32,3)

#### Results
- Epoch 50<br>
   ![epoch50](cifar10_trial1/gen_images/image_e_50.png)

- Epoch 100<br>
   ![epoch100](gen_images/image_e_100.png)

- Epoch 200<br>
   ![epoch200](gen_images/image_e_200.png)
