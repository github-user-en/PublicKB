1. **Image captioning**
   <u>User</u>: Please provide a one-sentence caption for the provided remote sensing image in details.
   <u>AI:</u> This urban image includes 8 tennis courts, a ground trackfield, and 4 vehicles.
   
2. **Region Caption**
   <u>User:</u> Please provide a short description for this region in this remote sensing image: [0.43,0.71,0.45,0.73]
   <u>AI:</u> A vehicle at the bottom.
   
3. **Visual Grounding**
   <u>User:</u> Please provide the horizontal bounding box coordinate of the region which is described as: the huge groundtrackfield on the upper right. 
   <u>AI:</u> [0.24,0.12,0.91,0.42].
   
4. **Scene Classification**
   <u>User:</u> What is the category of this remote sensing image? Answer the question using a single word or phrase. 
   <u>AI:</u> Stadium.

5. **Object Detection**
   <u>User:</u> Detect tennis courts shown in the image using horizontal bounding boxes.
   <u>AI:</u> There are eight tennis courts [0.12,0.50,0.16,0.59;0.19, 0.65,0.23,0.74;0.12,0.65, 0.16,0.74;0.34,0.50,0.38, 0.59;0.28,0.50,0.33,0.59; 0.23,0.50,0.27,0.59;0.17, 0.50,0.22,0.59;0.26,0.65, 0.30,0.74] in the image.
   
6. **Visual Question Answering**
   <u>User:</u> How many vehicles are there in this picture?
   <u>AI:</u> 4
   
7. **Multi-round Conversation**
   <u>User:</u> How many vehicles are there in this picture? Answer the question using a single word or phrase. 
   <u>AI:</u> ... 
   <u>User:</u> Detect tennis courts shown in the image using horizontal bounding box. 
   <u>AI:</u> .... 
   <u>User:</u> What is the category of this remote sensing image? 
   <u>EarthGPT:</u> ...

8. **Image Retrieval**
