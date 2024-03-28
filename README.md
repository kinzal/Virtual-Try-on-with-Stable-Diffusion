# Virtual-Try-on-with-Stable-Diffusion
Verwenden Sie Stable Diffusion, um eine virtuelle Umkleidekabine zu erstellen, die es Kunden ermöglicht, Kleidungsstücke digital anzuprobieren, bevor sie sie kaufen.
from PIL import Image

def virtual_try_on(person_image_path, clothing_image_path, output_path, clothing_position):
    """
    Simulate a virtual try-on by overlaying a clothing item on a person's image.
    
    Args:
    - person_image_path (str): Path to the image of the person.
    - clothing_image_path (str): Path to the image of the clothing item.
    - output_path (str): Path where the output image will be saved.
    - clothing_position (tuple): The (x, y) position where the top left corner of the clothing should be placed.
    """
    try:
        # Load images
        person_image = Image.open(person_image_path)
        clothing_image = Image.open(clothing_image_path)

        # Resize clothing image (this might need adjustment for different images)
        clothing_image = clothing_image.resize((200, 300))  # Example resizing, adjust as needed

        # Paste clothing image on the person image at the specified position
        person_image.paste(clothing_image, clothing_position, clothing_image)

        # Save the resulting image
        person_image.save(output_path)
        print(f"Virtual try-on image saved to {output_path}")
    except Exception as e:
        print(f"An error occurred: {e}")

# Example usage
virtual_try_on('person.jpg', 'tshirt.png', 'virtual_try_on_output.jpg', (100, 200))
