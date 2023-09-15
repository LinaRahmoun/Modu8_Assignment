# Modu8_Assignment
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.image.Image;
import javafx.scene.image.ImageView;
import javafx.scene.layout.HBox;
import javafx.stage.Stage;

import java.util.ArrayList;
import java.util.List;
import java.util.Random;

public class RandomCardDisplay extends Application {
    private static final int NUM_CARDS = 52;
    private static final int NUM_CARDS_TO_DISPLAY = 4;
    private static final String CARD_IMAGE_PATH = "cards/";

    public static void main(String[] args) {
        launch(args);
    }

    @Override
    public void start(Stage primaryStage) {
        primaryStage.setTitle("Random Card Display");

        List<Integer> selectedCardIndices = getRandomCardIndices(NUM_CARDS_TO_DISPLAY);

        HBox cardContainer = new HBox(10); // Horizontal box to display cards with spacing
        for (int cardIndex : selectedCardIndices) {
            String imagePath = CARD_IMAGE_PATH + (cardIndex + 1) + ".png"; // Card images are 1.png to 52.png
            Image cardImage = new Image("file:" + imagePath);
            ImageView cardView = new ImageView(cardImage);
            cardContainer.getChildren().add(cardView);
        }

        Scene scene = new Scene(cardContainer, 400, 150);
        primaryStage.setScene(scene);

        primaryStage.show();
    }

    private List<Integer> getRandomCardIndices(int numCards) {
        List<Integer> cardIndices = new ArrayList<>();
        Random random = new Random();

        while (cardIndices.size() < numCards) {
            int randomIndex = random.nextInt(NUM_CARDS); // Generate a random card index
            if (!cardIndices.contains(randomIndex)) {
                cardIndices.add(randomIndex);
            }
        }

        return cardIndices;
    }
}
