# Anushka-Das{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "X6A8Hm86UUZ-"
   },
   "source": [
    "**Prediction using Supervised ML**\n",
    "\n",
    "**Author: ANUSHKA DAS**\n",
    "\n",
    "**The task is done for the Data Science and Business Analytics Internshipnunder the GRIP by The Sparks Foundation\n",
    "(Februaury 2021)**\n",
    "\n",
    "**Creating a simple linear regression model with this Dataset and visualizing it graphically.**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "V9QN2ZxC38pB"
   },
   "outputs": [],
   "source": [
    "# Importing the libraries\n",
    "import pandas as pd\n",
    "import numpy as np  \n",
    "import matplotlib.pyplot as plt  \n",
    "%matplotlib inline"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 376
    },
    "colab_type": "code",
    "executionInfo": {
     "elapsed": 2534,
     "status": "ok",
     "timestamp": 1544113345787,
     "user": {
      "displayName": "A M Aditya",
      "photoUrl": "https://lh3.googleusercontent.com/-WI8p7JNWLic/AAAAAAAAAAI/AAAAAAAAAfs/vS8ElgH0p0c/s64/photo.jpg",
      "userId": "15341571102300750919"
     },
     "user_tz": -480
    },
    "id": "LtU4YMEhqm9m",
    "outputId": "5b4b36af-1545-497e-a6dc-7658bab71dbc"
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Data imported successfully\n"
     ]
    },
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Hours</th>\n",
       "      <th>Scores</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>2.5</td>\n",
       "      <td>21</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>5.1</td>\n",
       "      <td>47</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>3.2</td>\n",
       "      <td>27</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>8.5</td>\n",
       "      <td>75</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>3.5</td>\n",
       "      <td>30</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>5</th>\n",
       "      <td>1.5</td>\n",
       "      <td>20</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>6</th>\n",
       "      <td>9.2</td>\n",
       "      <td>88</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>7</th>\n",
       "      <td>5.5</td>\n",
       "      <td>60</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>8</th>\n",
       "      <td>8.3</td>\n",
       "      <td>81</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>9</th>\n",
       "      <td>2.7</td>\n",
       "      <td>25</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Hours  Scores\n",
       "0    2.5      21\n",
       "1    5.1      47\n",
       "2    3.2      27\n",
       "3    8.5      75\n",
       "4    3.5      30\n",
       "5    1.5      20\n",
       "6    9.2      88\n",
       "7    5.5      60\n",
       "8    8.3      81\n",
       "9    2.7      25"
      ]
     },
     "execution_count": 2,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Reading the data\n",
    "url = \"http://bit.ly/w-data\"\n",
    "s_data = pd.read_csv(url)\n",
    "print(\"Data imported successfully\")\n",
    "\n",
    "s_data.head(10)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 294
    },
    "colab_type": "code",
    "executionInfo": {
     "elapsed": 718,
     "status": "ok",
     "timestamp": 1544113350499,
     "user": {
      "displayName": "A M Aditya",
      "photoUrl": "https://lh3.googleusercontent.com/-WI8p7JNWLic/AAAAAAAAAAI/AAAAAAAAAfs/vS8ElgH0p0c/s64/photo.jpg",
      "userId": "15341571102300750919"
     },
     "user_tz": -480
    },
    "id": "qxYBZkhAqpn9",
    "outputId": "37264af1-786d-4e0c-a668-383264d1ddd1"
   },
   "outputs": [
    {
     "data": {
      "image/png": "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\nYII=\n",
      "text/plain": [
       "<matplotlib.figure.Figure at 0x7f463cea7f60>"
      ]
     },
     "metadata": {
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Plotting the scores\n",
    "s_data.plot(x='Hours', y='Scores', style='o')  \n",
    "plt.title('Hours vs Percentage')  \n",
    "plt.xlabel('Hours Studied')  \n",
    "plt.ylabel('Percentage Score')  \n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "fiQaULio4Rzr"
   },
   "source": [
    "From the graph above, we can see that there is a positive linear relation between the percentage of the scores and the number of hours studied."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "WWtEr64M4jdz"
   },
   "source": [
    "**Preparing the data and then dividing the data into attributes and labels.**\n",
    "\n",
    "Now, we will divide the train and test sets."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "LiJ5210e4tNX"
   },
   "outputs": [],
   "source": [
    "X = s_data.iloc[:, :-1].values  \n",
    "y = s_data.iloc[:, 1].values  "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "Riz-ZiZ34fO4"
   },
   "source": [
    "Now we have our attributes and labels, so the next step is to split the data into training and test sets. We will do this by using Scikit-Learn's method:"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "udFYso1M4BNw"
   },
   "outputs": [],
   "source": [
    "from sklearn.model_selection import train_test_split  \n",
    "X_train, X_test, y_train, y_test = train_test_split(X, y, \n",
    "                            test_size=0.2, random_state=0) "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "a6WXptFU5CkC"
   },
   "source": [
    "**Training the Algorithm**\n",
    "\n",
    "We have split our data into training and testing sets. Now we will train our algorithms. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 34
    },
    "colab_type": "code",
    "executionInfo": {
     "elapsed": 701,
     "status": "ok",
     "timestamp": 1544113358086,
     "user": {
      "displayName": "A M Aditya",
      "photoUrl": "https://lh3.googleusercontent.com/-WI8p7JNWLic/AAAAAAAAAAI/AAAAAAAAAfs/vS8ElgH0p0c/s64/photo.jpg",
      "userId": "15341571102300750919"
     },
     "user_tz": -480
    },
    "id": "qddCuaS84fpK",
    "outputId": "befbd977-772c-4bd1-bb48-ee5dd6bae73c"
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Training complete.\n"
     ]
    }
   ],
   "source": [
    "from sklearn.linear_model import LinearRegression  \n",
    "regressor = LinearRegression()  \n",
    "regressor.fit(X_train, y_train) \n",
    "\n",
    "print(\"Training complete.\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 265
    },
    "colab_type": "code",
    "executionInfo": {
     "elapsed": 985,
     "status": "ok",
     "timestamp": 1544113360867,
     "user": {
      "displayName": "A M Aditya",
      "photoUrl": "https://lh3.googleusercontent.com/-WI8p7JNWLic/AAAAAAAAAAI/AAAAAAAAAfs/vS8ElgH0p0c/s64/photo.jpg",
      "userId": "15341571102300750919"
     },
     "user_tz": -480
    },
    "id": "J61NX2_2-px7",
    "outputId": "d20ec1fd-3e2d-4eae-84a2-a0df57d31009"
   },
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<matplotlib.figure.Figure at 0x7f4637579d30>"
      ]
     },
     "metadata": {
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Plotting the regression line\n",
    "line = regressor.coef_*X+regressor.intercept_\n",
    "\n",
    "# Plotting for the test data\n",
    "plt.scatter(X, y)\n",
    "plt.plot(X, line);\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "JCQn-g4m5OK2"
   },
   "source": [
    "**Making Predictions**\n",
    "\n",
    "We have trained our algorithms. Now is the time for making some predictions."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 102
    },
    "colab_type": "code",
    "executionInfo": {
     "elapsed": 698,
     "status": "ok",
     "timestamp": 1544113363729,
     "user": {
      "displayName": "A M Aditya",
      "photoUrl": "https://lh3.googleusercontent.com/-WI8p7JNWLic/AAAAAAAAAAI/AAAAAAAAAfs/vS8ElgH0p0c/s64/photo.jpg",
      "userId": "15341571102300750919"
     },
     "user_tz": -480
    },
    "id": "Tt-Fmzu55EGM",
    "outputId": "46f1acf8-91ac-4984-cfbe-e614aa9ea849"
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "[[1.5]\n",
      " [3.2]\n",
      " [7.4]\n",
      " [2.5]\n",
      " [5.9]]\n"
     ]
    }
   ],
   "source": [
    "print(X_test) # Testing data - In Hours\n",
    "y_pred = regressor.predict(X_test) # Predicting the scores"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 204
    },
    "colab_type": "code",
    "executionInfo": {
     "elapsed": 753,
     "status": "ok",
     "timestamp": 1544113366918,
     "user": {
      "displayName": "A M Aditya",
      "photoUrl": "https://lh3.googleusercontent.com/-WI8p7JNWLic/AAAAAAAAAAI/AAAAAAAAAfs/vS8ElgH0p0c/s64/photo.jpg",
      "userId": "15341571102300750919"
     },
     "user_tz": -480
    },
    "id": "6bmZUMZh5QLb",
    "outputId": "8ea11a9e-c1b7-4fab-ab62-4dcbd2c8607b"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Actual</th>\n",
       "      <th>Predicted</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>20</td>\n",
       "      <td>16.884145</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>27</td>\n",
       "      <td>33.732261</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>69</td>\n",
       "      <td>75.357018</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>30</td>\n",
       "      <td>26.794801</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>62</td>\n",
       "      <td>60.491033</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Actual  Predicted\n",
       "0      20  16.884145\n",
       "1      27  33.732261\n",
       "2      69  75.357018\n",
       "3      30  26.794801\n",
       "4      62  60.491033"
      ]
     },
     "execution_count": 9,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Comparing Actual vs Predicted\n",
    "df = pd.DataFrame({'Actual': y_test, 'Predicted': y_pred})  \n",
    "df "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 51
    },
    "colab_type": "code",
    "executionInfo": {
     "elapsed": 862,
     "status": "ok",
     "timestamp": 1544113370494,
     "user": {
      "displayName": "A M Aditya",
      "photoUrl": "https://lh3.googleusercontent.com/-WI8p7JNWLic/AAAAAAAAAAI/AAAAAAAAAfs/vS8ElgH0p0c/s64/photo.jpg",
      "userId": "15341571102300750919"
     },
     "user_tz": -480
    },
    "id": "KAFO8zbx-AH1",
    "outputId": "fcb3830f-3cda-4dcb-f122-84b71f101fae"
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "No of Hours = 9.25\n",
      "Predicted Score = 93.69173248737539\n"
     ]
    }
   ],
   "source": [
    "# You can also test with your own data\n",
    "hours = 9.25\n",
    "own_pred = regressor.predict(hours)\n",
    "print(\"No of Hours = {}\".format(hours))\n",
    "print(\"Predicted Score = {}\".format(own_pred[0]))"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "0AAsPVA_6KmK"
   },
   "source": [
    "**Evaluating the model**\n",
    "\n",
    "The final step is to evaluate the performance of algorithm from our model. This is maainly done to compare how well the different algorithms perform on a particular dataset. So, we are going to use the mean square error. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {
     "base_uri": "https://localhost:8080/",
     "height": 34
    },
    "colab_type": "code",
    "executionInfo": {
     "elapsed": 834,
     "status": "ok",
     "timestamp": 1544113374919,
     "user": {
      "displayName": "A M Aditya",
      "photoUrl": "https://lh3.googleusercontent.com/-WI8p7JNWLic/AAAAAAAAAAI/AAAAAAAAAfs/vS8ElgH0p0c/s64/photo.jpg",
      "userId": "15341571102300750919"
     },
     "user_tz": -480
    },
    "id": "r5UOrRH-5VCQ",
    "outputId": "7b9ddcf1-2848-408f-d81f-7a60652c381e"
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Mean Absolute Error: 4.183859899002982\n"
     ]
    }
   ],
   "source": [
    "from sklearn import metrics  \n",
    "print('Mean Absolute Error:', \n",
    "      metrics.mean_absolute_error(y_test, y_pred)) "
   ]
  }
 ],
 "metadata": {
  "colab": {
   "collapsed_sections": [],
   "name": "Linear Regression.ipynb",
   "provenance": [
    {
     "file_id": "1wzD9Aa7cc7kRwyXq8DeJ8H56mJInOMZN",
     "timestamp": 1544113281508
    }
   ],
   "version": "0.3.2"
  },
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.8.5"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 1
}
