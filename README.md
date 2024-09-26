library(openair)
library(plorix)
RMSE(predictions_KNN, test.data$WQI)
RMSE(predictions_DT, test.data$WQI)
RMSE(predictions_RF, test.data$WQI)
RMSE(predictions_ANN, test.data$WQI)
RMSE(predictions_XGB, test.data$WQI)

std_dev_DT <- sd(predictions_DT)
corr_coef_DT <- cor(predictions_DT, test.data$WQI)

std_dev_RF <- sd(predictions_RF)
corr_coef_RF <- cor(predictions_RF, test.data$WQI)

std_dev_XGB <- sd(predictions_XGB)
corr_coef_XGB <- cor(predictions_XGB, test.data$WQI)

std_dev_KNN <- sd(predictions_KNN)
corr_coef_KNN <- cor(predictions_KNN, test.data$WQI)

std_dev_ANN <- sd(predictions_ANN)
corr_coef_ANN <- cor(predictions_ANN, test.data$WQI)


# Les données Observées (observed) et les prédictions pour chaque modèle (pred_*)
observed <- test.data$WQI

# Diagramme de Taylor
taylor.diagram(observed, predictions_DT, add=FALSE, col="red", pch=19, main="Taylor Diagram", pos.cor=TRUE)
taylor.diagram(observed, predictions_RF, add=TRUE, col="blue", pch=19)
taylor.diagram(observed, predictions_ANN, add=TRUE, col="green", pch=19)
taylor.diagram(observed, predictions_XGB, add=TRUE, col="purple", pch=19)
taylor.diagram(observed, predictions_KNN, add=TRUE, col="orange", pch=19)

# Ajouter une légende
legend("topright", legend=c("DT", "RF", "ANN", "XGB", "KNN"), col=c("red", "blue", "green", "purple", "orange"), pch=19)
