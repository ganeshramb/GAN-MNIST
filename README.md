# GAN-MNIST



Network : Discriminator<br>

input : (bs, 1, 28, 28)
      |                                                                                               ---- SUMMARY ----<br>
      V
Conv2d( in_channels = 1, out_channels = 16, kernel_size = (3,3), stride = 2)                           #(bs, 16, 13, 13)<br>
BatchNorm2d()                                                                                          #(bs, 16, 13, 13)<br>
LeakyReLU()                                                                                            #(bs, 16, 13, 13)<br>
      |<br>
      V<br>
Conv2d( in_channels = 16, out_channels = 32, kernel_size = (5,5), stride = 2)                          #(bs, 32, 5, 5)<br>
BatchNorm2d()                                                                                          #(bs, 32, 5, 5)<br>
LeakyReLU()                                                                                            #(bs, 32, 5, 5)<br>
      |<br>
      V<br>
Conv2d( in_channels = 32, out_channels = 64, kernel_size = (5,5), stride = 2)                          #(bs, 64, 1, 1)<br>
BatchNorm2d()                                                                                          #(bs, 64, 1, 1)<br>
LeakyReLU()                                                                                            #(bs, 64, 1, 1)<br>
      |<br>
      V<br>
Flatten()                                                                                              #(bs, 64)<br>
Linear(in_features = 64, out_features = 1)                                                             #(bs, 1)<br>





Network : Generator <br>

z_dim = 64<br>
input : (bs,z_dim)<br>

      |<br>
      | Reshape<br>
      V<br>

input : (bs, channel, height, width) -> (bs, z_dim , 1 , 1) <br>
      |                                                                                               ---- SUMMARY ----<br>
      V
ConvTranspose2d( in_channels = z_dim, out_channels = 256, kernel_size = (3,3), stride = 2)             #(bs, 256, 3, 3)<br>
BatchNorm2d()                                                                                          #(bs, 256, 3, 3)<br>
ReLU()                                                                                                 #(bs, 256, 3, 3)<br>
      |<br>
      V<br>
ConvTranspose2d( in_channels = 256, out_channels = 128, kernel_size = (4,4), stride = 1)               #(bs, 128, 6, 6)<br>
BatchNorm2d()                                                                                          #(bs, 128, 6, 6)<br>
ReLU()                                                                                                 #(bs, 128, 6, 6)<br>
      |<br>
      V<br>
ConvTranspose2d( in_channels = 128, out_channels = 64, kernel_size = (3,3), stride = 2)                #(bs, 64, 13, 13)<br>
BatchNorm2d()                                                                                          #(bs, 64, 13, 13)<br>
ReLU()                                                                                                 #(bs, 64, 13, 13)<br>
      |<br>
      V<br>
ConvTranspose2d( in_channels = 64, out_channels = 1, kernel_size = (4,4), stride = 2)                  #(bs, 1, 28, 28)<br>
Tanh()                                                                                                 #(bs, 1, 28, 28)<br>


