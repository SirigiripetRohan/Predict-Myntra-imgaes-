The project is about to Predict the images from myntra dataset , where target varaible are imgaes of 22 levels (Solid ,Typography,Striped,Graphic,Abstract ,Colourblocked         
,People and Places ,Geometric ,Floral  ,Conversational ,Tie and Dye,Varsity,Music,Biker,Camouflage,Humour and Comic,Superhero,Self Design,Tribal,Sports ,Checked ,Polka Dots)                       

Created the folders for each level of target varaibale and saved  all the images of that level in to respective folder .


Model Architecture :

We implemented CNN (Convolution Neural Networks ) on the image dataset as below 

# Model Architecture - Custom
model = Sequential()
model.add(Conv2D(32, (3, 3), input_shape=(150, 150, 3)))
model.add(Activation('relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))

took batch size of 32 

Data Augumentation:

train_datagen = ImageDataGenerator(
        rescale= None,
        shear_range=0.2,
        zoom_range=0.2,
        horizontal_flip=True)
        
total images in train and test is 
Found 5351 images belonging to 22 classes.
Found 1338 images belonging to 22 classes.

steps_per_epoch=5351//batch_size,
5351//32

Fitted the model on train_generater and predicted on test_generator 
Saved the model weights to h5 file for further use .
model.save_weights('WEIGHTS.h5')
From train_generator.class_indices pulled the labels which consists of levels(classes) and predictions like Solid:1, biker:2 and so....on as below mentioned .
From test_generator.class_indices pulled the labels which consists of levels(classes) and predictions like Solid:1, biker:2 and so....on as below mentioned .
labels = (test_generator.class_indices)
and also filenames associated to test_generator.

Evaluated the model on train_generator and could see accuracy of 0.65 and on test data is of 0.60
