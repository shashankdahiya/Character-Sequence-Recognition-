# Character-Sequence-Recognition

The work is based on Matthew Earl's [repository](https://github.com/matthewearl/deep-anpr).
Do follow his [blog post](http://matthewearl.github.io/2016/05/06/cnn-anpr/) to get an overview how he designed the sysytem.

### Improvement
Recognition of character from street view images with different environments .

## Data Augmentation

* How it now became very hard identification problem: 
	* Orientation
	* Font family
	* Different Pixel color of plate and that of whole image

We have more than **100,000 images** of around 36 GB 
We break data into 10,000 images batches for training

Consisting round *48 classes* of different locations

Also, our model is not only trained over GRAYSCALED images, 
rathar it includes synthesised images those are colored & gray as well for prediction on real images.

## Resnet Model

**CNN_1 Phase 1** | **CNN_2 Phase 2** | **Fully Connected layer**
------------|------------|-----------
*Step 1*      | *Detection* | *Decision*
 | | 
48 filter (128x64) In each, we find  **Pr[how_much_plate_is_in_the_frame]** by separating pixel by color | Move the stride over the layers to give the output a window coordinate, from which we can tell if a plate is in that stride as a whole | We use Relu function (like one hot encoding) to give the sequence from the Probability our model calculate
| |
*Step 2* 
| |
Find **Pr[the_character_in_the_plate_is_some_character_from_the_label]**

## Result

<img src="https://github.com/shashankdahiya/Character-Sequence-Recognition-/blob/master/Training_Accuracy.png" width="250"> | <img src="https://github.com/shashankdahiya/Character-Sequence-Recognition-/blob/master/out_4_1.jpg" width="250">
-----|------
 
