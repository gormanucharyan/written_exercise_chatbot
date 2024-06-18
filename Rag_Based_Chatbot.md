1. ## PDF Processor

    #### Chosen Tool: PyMuPDF
    
        Reason: PyMuPDF is known for its speed and accuracy in extracting text and metadata from PDFs. 
                It handles complex layouts well and is relatively easy to integrate with Python.
    
        Challenges:
    
            Some PDFs may have complex layouts with tables, images, and multi-column text.
    
            OCR (Optical Character Recognition) might be needed for scanned documents.
    
        Solutions: 
            
            Using the advanced features of PyMuPDF to parse different sections separately.
    
            Integrate Tesseract OCR or docTR for scanned documents to improve text extraction accuracy.
    
    #### Omitted Tool: Apache PDFBox
    
        Reason: It struggles in handling complex layouts which are common in installation manuals.
                Lack of OCR support, which would hepl process scanned documents.
                It's performance is slow which hinder the responsiveness of the chatbot.
                It is a Java library, making difficulties in integration within a Python-based system.

2. ## Vector Database
    
    #### Chosen Tool: Pinecone
    
        Reason: Pinecone offers a fully managed service, scalability, and ease of integration. 
                Capable of handling both text and image embeddings, which is crucial for our use case.
                It supports real-time updates and is optimized for low-latency searches, which is crucial for a responsive chatbot.
    
        Challenges:
            
            Cost Management: Pinecone can be expensive at scale.
    
        Solutions:
    
            Optimize the number of embeddings stored by preprocessing the text to remove redundant information and by using efficient embedding techniques.
    
    #### Omitted Tool: ElasticSearch
        
        Reason: Struggles with high-dimensional vectors.
    


3. ## Embedding Model

    #### Chosen Tool: OpenAI Embeddings
    
        Reason: OpenAI embeddings are known for their high accuracy and effectiveness in capturing semantic meaning, which is crucial for understanding and responding to user queries accurately.
    
        Challenges:
    
            OpenAI embeddings can have large vector sizes, which increases storage and retrieval time.
            
            Using OpenAI’s API might come with rate limits that can affect the system’s responsiveness.
    
        Solution: 
        
            Use dimensionality reduction techniques like PCA (Principal Component Analysis) to reduce the vector size without losing significant information.
    
            Implement a caching mechanism to store frequently used embeddings and reduce the number of API calls.

4. ## LLM generative model

    #### Chosen Tool: OpenAI GPT-4
    
        Reason: GPT-4 provides state-of-the-art performance in generating coherent and contextually relevant responses, making it suitable for a wide range of conversational tasks.
                It provides a lot of services, and agents (assistants) that you can give instructions as needed and use with API in your code.
    
        Challenges:

            Generating responses in real-time can introduce latency.
            
            Manuals often contain technical terms and jargon that might not be familiar to the LLM, potentially leading to misunderstandings or inaccurate responses.

    
        Solution:
     
            Use efficient prompt engineering and pre-processing steps to minimize the amount of data sent to the LLM, thereby reducing response time.

            Fine-Tuning with dataset of installation manuals and technical documents relevant to the domain or simply integrate a list of technical terms and their definitions into the system.

There is no ideal LLM model for embedding and generative tasks. Personally, I think OpenAI products are better. In case of using free resources, I would recommend Bert embeddings, Hugging Face which also has its datasets and models giving an opportunity to fine-tune, use APIs.

## Questions

In case of questions that require a long process to address the issue, the chatbot can be instructed in a way to break into subtasks the query, and step by step address all of them.
### LLM capable of it

1. How can I replace the water filter myself on the refrigerator?
2. What are the safety precautions when installing a new water heater?
3. How much power does a 'this brand' water heater consume?
4. What troubleshooting steps should I take if my air conditioner isn't blowing cold air?
5. The manual for my new air conditioner says to install it on a wall at least 15 cm from the ceiling and 30 cm from any corners. My living room is 'this' m^2 with a ceiling height of 'this' m. There's a sofa 'this' cm away from the wall, and chairs scattered around the room. Considering the room layout and furniture placement, what's the optimal location for the air conditioner to ensure efficient cooling, avoid uncomfortable drafts, and prevent getting sick from sitting directly in the cold airflow?"

##### These questions can be answered by chatbot, because they all share information in manual, which can be found. The last question might seem to be the most complex one, but as chatbots also have knowledge of sciences, it can measure all the necessarily values and parameters to ensure the optimal location.

### LLM will struggle with

1. What's the best brand of water heater?
2. My printer doesn't print, even though the ink cartridges are full. I've tried turning it off and on again, but it still doesn't work. What could be the problem?
3. The instructions for installing my new oven say to connect the gas line using a 1.5 cm flexible metal connector. However, my existing gas line appears to be a different size. Can I use an adapter to connect them?
4. Can I use this air conditioner model in a room with high humidity?
5. How much time will it take to install this dishwasher?

##### These questions are complex and will make chatbot to struggle, because they are related to personal experiences and preferences. Since among them, there are questions that have more than one answer, the chatbot cannot provide correct and direct answer. Also questions requiring knowledge beyond the manuals can make the model to provide wrong answers. In addition, it may happen that some information may be missing in the instructions, for example, when translating them from Japanese to English, you may lose information about voltage, and this loss of information will prevent the chatbot from responding to queries related to this concept.


 