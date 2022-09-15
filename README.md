# Tourists-Mobility-Patter-using-Twitter

{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "import pandas as pd\n",
    "import numpy as np\n",
    "import matplotlib.pyplot as plt\n",
    "from sklearn.cluster import KMeans\n",
    "import seaborn as sns; sns.set()\n",
    "import csv\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "metadata": {},
   "outputs": [],
   "source": [
    "df = pd.read_csv('delhi_w1_new_poojaesthetic_tweets.csv', encoding='utf-8')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 28,
   "metadata": {},
   }
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {},
   "outputs": [],
   "source": [
    "    import pandas as pd\n",
    "    import datetime\n",
    "    from shapely.geometry import Point, Polygon\n",
    "    import datetime\n",
    "    from shapely import wkt\n",
    "    import geopandas as gpd"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "\n",
    "\n",
    "            "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [],
   "source": [
    "    df = pd.read_csv(r'combined_residents.csv', encoding='utf-8')\n",
    "    df[df['coordinates'].notna()]\n",
    "    df['coordinates'] = df.coordinates.str.replace('type,?' , '')\n",
    "    df['coordinates'] = df.coordinates.str.replace('Point,?' , '')\n",
    "    df['coordinates'] = df.coordinates.str.replace('coordinates,?' , '')\n",
    "    df['coordinates'] = df.coordinates.str.replace('{,?' , '')\n",
    "    df['coordinates'] = df.coordinates.str.replace(':,?' , '')\n",
    "    df['coordinates'] = df.coordinates.str.replace('\\],?' , '')\n",
    "    df['coordinates'] = df.coordinates.str.replace(',?' , '')\n",
    "    df['coordinates'] = df.coordinates.str.replace('},?' , '')\n",
    "    df['coordinates'] = df.coordinates.str.replace(\"'',?\" , \"\")\n",
    "    df['coordinates'] = df.coordinates.str.replace('\\[,?' , '')\n",
    "    df[['a','b','c','LON','LAT']] = df.coordinates.str.split(\" \",expand=True,)\n",
    "    df.drop(['a', 'b','c'], axis = 1)\n",
    "    df.dropna(subset = [\"LAT\"], inplace=True)\n",
    "    df['LON'] = pd.to_numeric(df['LON'],errors='coerce')\n",
    "    df['LAT'] = pd.to_numeric(df['LAT'],errors='coerce')\n",
    "    df.dropna(subset = [\"LAT\"], inplace=True)\n",
    "    "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [],
   "source": [
    "    from shapely.geometry import Point, Polygon\n",
    "    import datetime\n",
    "    from shapely import wkt\n",
    "    import geopandas as gpd\n",
    "    from shapely.geometry import Point, Polygon\n",
    "    def check(p):\n",
    "        from shapely.geometry import Point, Polygon\n",
    "        # Create a Polygon\n",
    "        coords = coords = [(77.15, 28.45), (77.30, 28.45), (77.15, 29), (77.30, 29)]\n",
    "        poly = Polygon(coords)\n",
    "        y = p.within(poly)\n",
    "        return(y)\n",
    "    gdf = gpd.GeoDataFrame(df, geometry=gpd.points_from_xy(df.LON, df.LAT))\n",
    "    df['val']=df['geometry'].apply(check)\n",
    "\n",
    "    \n",
    "    \n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {},
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
       "      <th>id</th>\n",
       "      <th>created_at</th>\n",
       "      <th>text</th>\n",
       "      <th>coordinates</th>\n",
       "      <th>user_described_location</th>\n",
       "      <th>a</th>\n",
       "      <th>b</th>\n",
       "      <th>c</th>\n",
       "      <th>LON</th>\n",
       "      <th>LAT</th>\n",
       "      <th>geometry</th>\n",
       "      <th>val</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>12</th>\n",
       "      <td>1311073726755151882</td>\n",
       "      <td>2020-09-29 22:41:49</td>\n",
       "      <td>Just posted a photo @ Delhi, India https://t.c...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>13</th>\n",
       "      <td>1311073457854189568</td>\n",
       "      <td>2020-09-29 22:40:45</td>\n",
       "      <td>Just posted a photo @ Delhi, India https://t.c...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>14</th>\n",
       "      <td>1311073146590711808</td>\n",
       "      <td>2020-09-29 22:39:31</td>\n",
       "      <td>Just posted a photo @ Delhi, India https://t.c...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>15</th>\n",
       "      <td>1311072899659427845</td>\n",
       "      <td>2020-09-29 22:38:32</td>\n",
       "      <td>Just posted a photo @ Delhi, India https://t.c...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>16</th>\n",
       "      <td>1311072586177163271</td>\n",
       "      <td>2020-09-29 22:37:17</td>\n",
       "      <td>Just posted a photo @ Delhi, India https://t.c...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>721516</th>\n",
       "      <td>1022694031954989056</td>\n",
       "      <td>2018-07-27 04:03:52</td>\n",
       "      <td>Studio  Opening soon Freinds.. #ysipa #yuvhraj...</td>\n",
       "      <td>77.2089 28.6139</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.208900</td>\n",
       "      <td>28.613900</td>\n",
       "      <td>POINT (77.20890 28.61390)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>721519</th>\n",
       "      <td>1022446299705225217</td>\n",
       "      <td>2018-07-26 11:39:28</td>\n",
       "      <td>Studio  Opening soon Freinds.. #ysipa #yuvhraj...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>722638</th>\n",
       "      <td>1316469492860383232</td>\n",
       "      <td>2020-10-14 20:02:40</td>\n",
       "      <td>ＧＯＬＤＥＮ @ Somewhere on Planet Earth https://t.c...</td>\n",
       "      <td>77.21728 28.63096</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.217280</td>\n",
       "      <td>28.630960</td>\n",
       "      <td>POINT (77.21728 28.63096)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>722639</th>\n",
       "      <td>1316338359237783552</td>\n",
       "      <td>2020-10-14 11:21:35</td>\n",
       "      <td>ＳＨＩＮＥ @ Somewhere on Planet Earth https://t.co...</td>\n",
       "      <td>77.21728 28.63096</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.217280</td>\n",
       "      <td>28.630960</td>\n",
       "      <td>POINT (77.21728 28.63096)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>722641</th>\n",
       "      <td>1316156812798943232</td>\n",
       "      <td>2020-10-13 23:20:11</td>\n",
       "      <td>ＧＯＬＤＥＮ @ Somewhere on Planet Earth https://t.c...</td>\n",
       "      <td>77.21728 28.63096</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.217280</td>\n",
       "      <td>28.630960</td>\n",
       "      <td>POINT (77.21728 28.63096)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>46191 rows × 12 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "                         id           created_at  \\\n",
       "12      1311073726755151882  2020-09-29 22:41:49   \n",
       "13      1311073457854189568  2020-09-29 22:40:45   \n",
       "14      1311073146590711808  2020-09-29 22:39:31   \n",
       "15      1311072899659427845  2020-09-29 22:38:32   \n",
       "16      1311072586177163271  2020-09-29 22:37:17   \n",
       "...                     ...                  ...   \n",
       "721516  1022694031954989056  2018-07-27 04:03:52   \n",
       "721519  1022446299705225217  2018-07-26 11:39:28   \n",
       "722638  1316469492860383232  2020-10-14 20:02:40   \n",
       "722639  1316338359237783552  2020-10-14 11:21:35   \n",
       "722641  1316156812798943232  2020-10-13 23:20:11   \n",
       "\n",
       "                                                     text  \\\n",
       "12      Just posted a photo @ Delhi, India https://t.c...   \n",
       "13      Just posted a photo @ Delhi, India https://t.c...   \n",
       "14      Just posted a photo @ Delhi, India https://t.c...   \n",
       "15      Just posted a photo @ Delhi, India https://t.c...   \n",
       "16      Just posted a photo @ Delhi, India https://t.c...   \n",
       "...                                                   ...   \n",
       "721516  Studio  Opening soon Freinds.. #ysipa #yuvhraj...   \n",
       "721519  Studio  Opening soon Freinds.. #ysipa #yuvhraj...   \n",
       "722638  ＧＯＬＤＥＮ @ Somewhere on Planet Earth https://t.c...   \n",
       "722639  ＳＨＩＮＥ @ Somewhere on Planet Earth https://t.co...   \n",
       "722641  ＧＯＬＤＥＮ @ Somewhere on Planet Earth https://t.c...   \n",
       "\n",
       "                   coordinates  user_described_location a  b  c         LON  \\\n",
       "12         77.219672 28.631747                      NaN           77.219672   \n",
       "13         77.219672 28.631747                      NaN           77.219672   \n",
       "14         77.219672 28.631747                      NaN           77.219672   \n",
       "15         77.219672 28.631747                      NaN           77.219672   \n",
       "16         77.219672 28.631747                      NaN           77.219672   \n",
       "...                        ...                      ... .. .. ..        ...   \n",
       "721516         77.2089 28.6139                      NaN           77.208900   \n",
       "721519     77.219672 28.631747                      NaN           77.219672   \n",
       "722638       77.21728 28.63096                      NaN           77.217280   \n",
       "722639       77.21728 28.63096                      NaN           77.217280   \n",
       "722641       77.21728 28.63096                      NaN           77.217280   \n",
       "\n",
       "              LAT                   geometry   val  \n",
       "12      28.631747  POINT (77.21967 28.63175)  True  \n",
       "13      28.631747  POINT (77.21967 28.63175)  True  \n",
       "14      28.631747  POINT (77.21967 28.63175)  True  \n",
       "15      28.631747  POINT (77.21967 28.63175)  True  \n",
       "16      28.631747  POINT (77.21967 28.63175)  True  \n",
       "...           ...                        ...   ...  \n",
       "721516  28.613900  POINT (77.20890 28.61390)  True  \n",
       "721519  28.631747  POINT (77.21967 28.63175)  True  \n",
       "722638  28.630960  POINT (77.21728 28.63096)  True  \n",
       "722639  28.630960  POINT (77.21728 28.63096)  True  \n",
       "722641  28.630960  POINT (77.21728 28.63096)  True  \n",
       "\n",
       "[46191 rows x 12 columns]"
      ]
     },
     "execution_count": 7,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.drop(df[df['val'] == False].index, inplace=True)\n",
    "df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {},
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
       "      <th>id</th>\n",
       "      <th>LAT</th>\n",
       "      <th>LON</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>12</th>\n",
       "      <td>1311073726755151882</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>13</th>\n",
       "      <td>1311073457854189568</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>14</th>\n",
       "      <td>1311073146590711808</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>15</th>\n",
       "      <td>1311072899659427845</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>16</th>\n",
       "      <td>1311072586177163271</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>17</th>\n",
       "      <td>1311072296434630658</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>18</th>\n",
       "      <td>1311072000580808704</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>19</th>\n",
       "      <td>1311071678445899776</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>20</th>\n",
       "      <td>1311055983775375361</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>23</th>\n",
       "      <td>1311037421455159296</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                     id        LAT        LON\n",
       "12  1311073726755151882  28.631747  77.219672\n",
       "13  1311073457854189568  28.631747  77.219672\n",
       "14  1311073146590711808  28.631747  77.219672\n",
       "15  1311072899659427845  28.631747  77.219672\n",
       "16  1311072586177163271  28.631747  77.219672\n",
       "17  1311072296434630658  28.631747  77.219672\n",
       "18  1311072000580808704  28.631747  77.219672\n",
       "19  1311071678445899776  28.631747  77.219672\n",
       "20  1311055983775375361  28.631747  77.219672\n",
       "23  1311037421455159296  28.631747  77.219672"
      ]
     },
     "execution_count": 8,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Variable with the Longitude and Latitude\n",
    "X=df.loc[:,['id','LAT','LON']]\n",
    "X.head(10)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "array([[28.65638698, 77.23703704],\n",
       "       [28.65607021, 77.24079609],\n",
       "       [28.65638698, 77.23703704],\n",
       "       ...,\n",
       "       [28.56540475, 77.18439333],\n",
       "       [28.56540475, 77.18439333],\n",
       "       [28.56540475, 77.18439333]])"
      ]
     },
     "execution_count": 7,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "X.to_numpy()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {},
   "outputs": [
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "C:\\Users\\user1\\Anaconda3\\lib\\site-packages\\statsmodels\\tools\\_testing.py:19: FutureWarning: pandas.util.testing is deprecated. Use the functions in the public API at pandas.testing instead.\n",
      "  import pandas.util.testing as tm\n"
     ]
    }
   ],
   "source": [
    "from kneed import KneeLocator\n",
    "\n",
    "\n",
    "from sklearn.cluster import KMeans, DBSCAN, MeanShift\n",
    "from sklearn.metrics import silhouette_score\n",
    "from sklearn.metrics import adjusted_rand_score\n",
    "\n",
    "\n",
    "\n",
    "\n",
    "import pandas as pd # working with data\n",
    "import numpy as np # working with arrays\n",
    "import matplotlib.pyplot as plt # visualization\n",
    "import seaborn as sb # visualization\n",
    "from mpl_toolkits.mplot3d import Axes3D # 3d plot\n",
    "from termcolor import colored as cl # text customization\n",
    "\n",
    "from sklearn.preprocessing import StandardScaler # data normalization"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "#now i am going to check the no of cluster needed our data by using elbow method\n",
    "Error =[]\n",
    "for i in range(1, 25):\n",
    "    kmeans = KMeans(n_clusters = i).fit(X)\n",
    "    kmeans.fit(X)\n",
    "    Error.append(kmeans.inertia_)\n",
    "import matplotlib.pyplot as plt\n",
    "plt.plot(Error,range(1, 25))\n",
    "plt.title('Elbow method')\n",
    "plt.xlabel('Error')\n",
    "plt.ylabel('No of clusters')\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {},
   "outputs": [],
   "source": [
    "K_clusters = range(1,50)\n",
    "\n",
    "kmeans = [KMeans(n_clusters=i) for i in K_clusters]\n",
    "\n",
    "Y_axis = df[['LAT']]\n",
    "X_axis = df[['LON']]\n",
    "\n",
    "score = [kmeans[i].fit(Y_axis).score(Y_axis) for i in range(len(kmeans))]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "plt.plot(K_clusters, score)\n",
    "plt.xlabel('Number of Clusters')\n",
    "\n",
    "plt.ylabel('Score')\n",
    "\n",
    "plt.title('Elbow Curve')\n",
    "\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "metadata": {},
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
       "      <th>id</th>\n",
       "      <th>LAT</th>\n",
       "      <th>LON</th>\n",
       "      <th>cluster_label</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>12</th>\n",
       "      <td>1311073726755151882</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>13</th>\n",
       "      <td>1311073457854189568</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>14</th>\n",
       "      <td>1311073146590711808</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>15</th>\n",
       "      <td>1311072899659427845</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>16</th>\n",
       "      <td>1311072586177163271</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>17</th>\n",
       "      <td>1311072296434630658</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>18</th>\n",
       "      <td>1311072000580808704</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>19</th>\n",
       "      <td>1311071678445899776</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>20</th>\n",
       "      <td>1311055983775375361</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>23</th>\n",
       "      <td>1311037421455159296</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>77.219672</td>\n",
       "      <td>0</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                     id        LAT        LON  cluster_label\n",
       "12  1311073726755151882  28.631747  77.219672              0\n",
       "13  1311073457854189568  28.631747  77.219672              0\n",
       "14  1311073146590711808  28.631747  77.219672              0\n",
       "15  1311072899659427845  28.631747  77.219672              0\n",
       "16  1311072586177163271  28.631747  77.219672              0\n",
       "17  1311072296434630658  28.631747  77.219672              0\n",
       "18  1311072000580808704  28.631747  77.219672              0\n",
       "19  1311071678445899776  28.631747  77.219672              0\n",
       "20  1311055983775375361  28.631747  77.219672              0\n",
       "23  1311037421455159296  28.631747  77.219672              0"
      ]
     },
     "execution_count": 14,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "kmeans = KMeans(n_clusters = 11, init ='k-means++')\n",
    "kmeans.fit(X[X.columns[1:3]]) # Compute k-means clustering.\n",
    "X['cluster_label'] = kmeans.fit_predict(X[X.columns[1:3]])\n",
    "centers = kmeans.cluster_centers_ # Coordinates of cluster centers.\n",
    "labels = kmeans.predict(X[X.columns[1:3]]) # Labels of each point\n",
    "X.head(10)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "{0.8043227007158713}\n"
     ]
    }
   ],
   "source": [
    "from sklearn.metrics import silhouette_score\n",
    "label=kmeans.predict(X[X.columns[1:3]])\n",
    "print({silhouette_score(X[X.columns[1:3]], label)})\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 16,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "257175.91300942484"
      ]
     },
     "execution_count": 16,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#Calinski Harabasz\n",
    "from sklearn.metrics import calinski_harabasz_score\n",
    "kmeans_calinski_harabasz_score = calinski_harabasz_score(X[X.columns[1:3]], label)\n",
    "kmeans_calinski_harabasz_score\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 17,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0.47697382077426426"
      ]
     },
     "execution_count": 17,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#davies_bouldin_score\n",
    "\n",
    "from sklearn.metrics import davies_bouldin_score\n",
    "\n",
    "kmeans_davies_bouldin_score = davies_bouldin_score(X[X.columns[1:3]], label)\n",
    "\n",
    "kmeans_davies_bouldin_score"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.collections.PathCollection at 0x1b0c5859b48>"
      ]
     },
     "execution_count": 18,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 2 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "X.plot.scatter(x = 'LAT', y = 'LON', c=labels, s=50, cmap='viridis')\n",
    "plt.scatter(centers[:, 0], centers[:, 1], c='black', s=200, alpha=0.5)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 19,
   "metadata": {},
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
       "      <th>id</th>\n",
       "      <th>created_at</th>\n",
       "      <th>text</th>\n",
       "      <th>coordinates</th>\n",
       "      <th>user_described_location</th>\n",
       "      <th>a</th>\n",
       "      <th>b</th>\n",
       "      <th>c</th>\n",
       "      <th>LON</th>\n",
       "      <th>LAT</th>\n",
       "      <th>geometry</th>\n",
       "      <th>val</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>12</th>\n",
       "      <td>1311073726755151882</td>\n",
       "      <td>2020-09-29 22:41:49</td>\n",
       "      <td>Just posted a photo @ Delhi, India https://t.c...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>13</th>\n",
       "      <td>1311073457854189568</td>\n",
       "      <td>2020-09-29 22:40:45</td>\n",
       "      <td>Just posted a photo @ Delhi, India https://t.c...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>14</th>\n",
       "      <td>1311073146590711808</td>\n",
       "      <td>2020-09-29 22:39:31</td>\n",
       "      <td>Just posted a photo @ Delhi, India https://t.c...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>15</th>\n",
       "      <td>1311072899659427845</td>\n",
       "      <td>2020-09-29 22:38:32</td>\n",
       "      <td>Just posted a photo @ Delhi, India https://t.c...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>16</th>\n",
       "      <td>1311072586177163271</td>\n",
       "      <td>2020-09-29 22:37:17</td>\n",
       "      <td>Just posted a photo @ Delhi, India https://t.c...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                     id           created_at  \\\n",
       "12  1311073726755151882  2020-09-29 22:41:49   \n",
       "13  1311073457854189568  2020-09-29 22:40:45   \n",
       "14  1311073146590711808  2020-09-29 22:39:31   \n",
       "15  1311072899659427845  2020-09-29 22:38:32   \n",
       "16  1311072586177163271  2020-09-29 22:37:17   \n",
       "\n",
       "                                                 text             coordinates  \\\n",
       "12  Just posted a photo @ Delhi, India https://t.c...     77.219672 28.631747   \n",
       "13  Just posted a photo @ Delhi, India https://t.c...     77.219672 28.631747   \n",
       "14  Just posted a photo @ Delhi, India https://t.c...     77.219672 28.631747   \n",
       "15  Just posted a photo @ Delhi, India https://t.c...     77.219672 28.631747   \n",
       "16  Just posted a photo @ Delhi, India https://t.c...     77.219672 28.631747   \n",
       "\n",
       "    user_described_location a b c        LON        LAT  \\\n",
       "12                      NaN        77.219672  28.631747   \n",
       "13                      NaN        77.219672  28.631747   \n",
       "14                      NaN        77.219672  28.631747   \n",
       "15                      NaN        77.219672  28.631747   \n",
       "16                      NaN        77.219672  28.631747   \n",
       "\n",
       "                     geometry   val  \n",
       "12  POINT (77.21967 28.63175)  True  \n",
       "13  POINT (77.21967 28.63175)  True  \n",
       "14  POINT (77.21967 28.63175)  True  \n",
       "15  POINT (77.21967 28.63175)  True  \n",
       "16  POINT (77.21967 28.63175)  True  "
      ]
     },
     "execution_count": 19,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.head(5)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 20,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "[[28.63144458 77.21953544]\n",
      " [28.54138556 77.24506995]\n",
      " [28.94516196 77.22062514]\n",
      " [28.57056271 77.2342431 ]\n",
      " [28.52991462 77.21722189]\n",
      " [28.64780789 77.23856188]\n",
      " [28.61313776 77.20839486]\n",
      " [28.55805255 77.20151848]\n",
      " [28.51085302 77.18358128]\n",
      " [28.60198504 77.23413097]\n",
      " [28.66667993 77.21695771]]\n"
     ]
    }
   ],
   "source": [
    "centers = kmeans.cluster_centers_\n",
    "print(centers)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "metadata": {},
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
       "      <th>id</th>\n",
       "      <th>created_at</th>\n",
       "      <th>text</th>\n",
       "      <th>coordinates</th>\n",
       "      <th>user_described_location</th>\n",
       "      <th>a</th>\n",
       "      <th>b</th>\n",
       "      <th>c</th>\n",
       "      <th>LON</th>\n",
       "      <th>LAT</th>\n",
       "      <th>geometry</th>\n",
       "      <th>val</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>12</th>\n",
       "      <td>1311073726755151882</td>\n",
       "      <td>2020-09-29 22:41:49</td>\n",
       "      <td>Just posted a photo @ Delhi, India https://t.c...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>13</th>\n",
       "      <td>1311073457854189568</td>\n",
       "      <td>2020-09-29 22:40:45</td>\n",
       "      <td>Just posted a photo @ Delhi, India https://t.c...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>14</th>\n",
       "      <td>1311073146590711808</td>\n",
       "      <td>2020-09-29 22:39:31</td>\n",
       "      <td>Just posted a photo @ Delhi, India https://t.c...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>15</th>\n",
       "      <td>1311072899659427845</td>\n",
       "      <td>2020-09-29 22:38:32</td>\n",
       "      <td>Just posted a photo @ Delhi, India https://t.c...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>16</th>\n",
       "      <td>1311072586177163271</td>\n",
       "      <td>2020-09-29 22:37:17</td>\n",
       "      <td>Just posted a photo @ Delhi, India https://t.c...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>721516</th>\n",
       "      <td>1022694031954989056</td>\n",
       "      <td>2018-07-27 04:03:52</td>\n",
       "      <td>Studio  Opening soon Freinds.. #ysipa #yuvhraj...</td>\n",
       "      <td>77.2089 28.6139</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.208900</td>\n",
       "      <td>28.613900</td>\n",
       "      <td>POINT (77.20890 28.61390)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>721519</th>\n",
       "      <td>1022446299705225217</td>\n",
       "      <td>2018-07-26 11:39:28</td>\n",
       "      <td>Studio  Opening soon Freinds.. #ysipa #yuvhraj...</td>\n",
       "      <td>77.219672 28.631747</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.219672</td>\n",
       "      <td>28.631747</td>\n",
       "      <td>POINT (77.21967 28.63175)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>722638</th>\n",
       "      <td>1316469492860383232</td>\n",
       "      <td>2020-10-14 20:02:40</td>\n",
       "      <td>ＧＯＬＤＥＮ @ Somewhere on Planet Earth https://t.c...</td>\n",
       "      <td>77.21728 28.63096</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.217280</td>\n",
       "      <td>28.630960</td>\n",
       "      <td>POINT (77.21728 28.63096)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>722639</th>\n",
       "      <td>1316338359237783552</td>\n",
       "      <td>2020-10-14 11:21:35</td>\n",
       "      <td>ＳＨＩＮＥ @ Somewhere on Planet Earth https://t.co...</td>\n",
       "      <td>77.21728 28.63096</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.217280</td>\n",
       "      <td>28.630960</td>\n",
       "      <td>POINT (77.21728 28.63096)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>722641</th>\n",
       "      <td>1316156812798943232</td>\n",
       "      <td>2020-10-13 23:20:11</td>\n",
       "      <td>ＧＯＬＤＥＮ @ Somewhere on Planet Earth https://t.c...</td>\n",
       "      <td>77.21728 28.63096</td>\n",
       "      <td>NaN</td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td></td>\n",
       "      <td>77.217280</td>\n",
       "      <td>28.630960</td>\n",
       "      <td>POINT (77.21728 28.63096)</td>\n",
       "      <td>True</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>46191 rows × 12 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "                         id           created_at  \\\n",
       "12      1311073726755151882  2020-09-29 22:41:49   \n",
       "13      1311073457854189568  2020-09-29 22:40:45   \n",
       "14      1311073146590711808  2020-09-29 22:39:31   \n",
       "15      1311072899659427845  2020-09-29 22:38:32   \n",
       "16      1311072586177163271  2020-09-29 22:37:17   \n",
       "...                     ...                  ...   \n",
       "721516  1022694031954989056  2018-07-27 04:03:52   \n",
       "721519  1022446299705225217  2018-07-26 11:39:28   \n",
       "722638  1316469492860383232  2020-10-14 20:02:40   \n",
       "722639  1316338359237783552  2020-10-14 11:21:35   \n",
       "722641  1316156812798943232  2020-10-13 23:20:11   \n",
       "\n",
       "                                                     text  \\\n",
       "12      Just posted a photo @ Delhi, India https://t.c...   \n",
       "13      Just posted a photo @ Delhi, India https://t.c...   \n",
       "14      Just posted a photo @ Delhi, India https://t.c...   \n",
       "15      Just posted a photo @ Delhi, India https://t.c...   \n",
       "16      Just posted a photo @ Delhi, India https://t.c...   \n",
       "...                                                   ...   \n",
       "721516  Studio  Opening soon Freinds.. #ysipa #yuvhraj...   \n",
       "721519  Studio  Opening soon Freinds.. #ysipa #yuvhraj...   \n",
       "722638  ＧＯＬＤＥＮ @ Somewhere on Planet Earth https://t.c...   \n",
       "722639  ＳＨＩＮＥ @ Somewhere on Planet Earth https://t.co...   \n",
       "722641  ＧＯＬＤＥＮ @ Somewhere on Planet Earth https://t.c...   \n",
       "\n",
       "                   coordinates  user_described_location a  b  c         LON  \\\n",
       "12         77.219672 28.631747                      NaN           77.219672   \n",
       "13         77.219672 28.631747                      NaN           77.219672   \n",
       "14         77.219672 28.631747                      NaN           77.219672   \n",
       "15         77.219672 28.631747                      NaN           77.219672   \n",
       "16         77.219672 28.631747                      NaN           77.219672   \n",
       "...                        ...                      ... .. .. ..        ...   \n",
       "721516         77.2089 28.6139                      NaN           77.208900   \n",
       "721519     77.219672 28.631747                      NaN           77.219672   \n",
       "722638       77.21728 28.63096                      NaN           77.217280   \n",
       "722639       77.21728 28.63096                      NaN           77.217280   \n",
       "722641       77.21728 28.63096                      NaN           77.217280   \n",
       "\n",
       "              LAT                   geometry   val  \n",
       "12      28.631747  POINT (77.21967 28.63175)  True  \n",
       "13      28.631747  POINT (77.21967 28.63175)  True  \n",
       "14      28.631747  POINT (77.21967 28.63175)  True  \n",
       "15      28.631747  POINT (77.21967 28.63175)  True  \n",
       "16      28.631747  POINT (77.21967 28.63175)  True  \n",
       "...           ...                        ...   ...  \n",
       "721516  28.613900  POINT (77.20890 28.61390)  True  \n",
       "721519  28.631747  POINT (77.21967 28.63175)  True  \n",
       "722638  28.630960  POINT (77.21728 28.63096)  True  \n",
       "722639  28.630960  POINT (77.21728 28.63096)  True  \n",
       "722641  28.630960  POINT (77.21728 28.63096)  True  \n",
       "\n",
       "[46191 rows x 12 columns]"
      ]
     },
     "execution_count": 21,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "import pandas as pd, numpy as np, matplotlib.pyplot as plt\n",
    "from sklearn.cluster import DBSCAN\n",
    "from geopy.distance import great_circle\n",
    "from shapely.geometry import MultiPoint\n",
    "coords = df[['LAT', 'LON']].values\n",
    "df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Number of clusters: 6\n"
     ]
    }
   ],
   "source": [
    "kms_per_radian = 6371.0088\n",
    "epsilon = 1.5 / kms_per_radian\n",
    "db = DBSCAN(eps=epsilon, min_samples=2, algorithm='ball_tree', metric='haversine').fit(np.radians(coords))\n",
    "cluster_labels = db.labels_\n",
    "num_clusters = len(set(cluster_labels))\n",
    "clusters = pd.Series([coords[cluster_labels == n] for n in range(num_clusters)])\n",
    "print('Number of clusters: {}'.format(num_clusters))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 23,
   "metadata": {},
   "outputs": [
    {
     "ename": "IndexError",
     "evalue": "list index out of range",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mIndexError\u001b[0m                                Traceback (most recent call last)",
      "\u001b[1;32m<ipython-input-23-603247548f70>\u001b[0m in \u001b[0;36m<module>\u001b[1;34m\u001b[0m\n\u001b[0;32m      3\u001b[0m     \u001b[0mcentermost_point\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mmin\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mcluster\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mkey\u001b[0m\u001b[1;33m=\u001b[0m\u001b[1;32mlambda\u001b[0m \u001b[0mpoint\u001b[0m\u001b[1;33m:\u001b[0m \u001b[0mgreat_circle\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mpoint\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mcentroid\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mm\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m      4\u001b[0m     \u001b[1;32mreturn\u001b[0m \u001b[0mtuple\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mcentermost_point\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m----> 5\u001b[1;33m \u001b[0mcentermost_points\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mclusters\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mmap\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mget_centermost_point\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m",
      "\u001b[1;32m~\\Anaconda3\\lib\\site-packages\\pandas\\core\\series.py\u001b[0m in \u001b[0;36mmap\u001b[1;34m(self, arg, na_action)\u001b[0m\n\u001b[0;32m   3980\u001b[0m         \u001b[0mdtype\u001b[0m\u001b[1;33m:\u001b[0m \u001b[0mobject\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m   3981\u001b[0m         \"\"\"\n\u001b[1;32m-> 3982\u001b[1;33m         \u001b[0mnew_values\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0msuper\u001b[0m\u001b[1;33m(\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0m_map_values\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0marg\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mna_action\u001b[0m\u001b[1;33m=\u001b[0m\u001b[0mna_action\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m\u001b[0;32m   3983\u001b[0m         return self._constructor(new_values, index=self.index).__finalize__(\n\u001b[0;32m   3984\u001b[0m             \u001b[0mself\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mmethod\u001b[0m\u001b[1;33m=\u001b[0m\u001b[1;34m\"map\"\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n",
      "\u001b[1;32m~\\Anaconda3\\lib\\site-packages\\pandas\\core\\base.py\u001b[0m in \u001b[0;36m_map_values\u001b[1;34m(self, mapper, na_action)\u001b[0m\n\u001b[0;32m   1158\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m   1159\u001b[0m         \u001b[1;31m# mapper is a function\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m-> 1160\u001b[1;33m         \u001b[0mnew_values\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mmap_f\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mvalues\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mmapper\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m\u001b[0;32m   1161\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m   1162\u001b[0m         \u001b[1;32mreturn\u001b[0m \u001b[0mnew_values\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n",
      "\u001b[1;32mpandas\\_libs\\lib.pyx\u001b[0m in \u001b[0;36mpandas._libs.lib.map_infer\u001b[1;34m()\u001b[0m\n",
      "\u001b[1;32m<ipython-input-23-603247548f70>\u001b[0m in \u001b[0;36mget_centermost_point\u001b[1;34m(cluster)\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[1;32mdef\u001b[0m \u001b[0mget_centermost_point\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mcluster\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m:\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m----> 2\u001b[1;33m     \u001b[0mcentroid\u001b[0m \u001b[1;33m=\u001b[0m \u001b[1;33m(\u001b[0m\u001b[0mMultiPoint\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mcluster\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mcentroid\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mx\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mMultiPoint\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mcluster\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mcentroid\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0my\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m\u001b[0;32m      3\u001b[0m     \u001b[0mcentermost_point\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mmin\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mcluster\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mkey\u001b[0m\u001b[1;33m=\u001b[0m\u001b[1;32mlambda\u001b[0m \u001b[0mpoint\u001b[0m\u001b[1;33m:\u001b[0m \u001b[0mgreat_circle\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mpoint\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mcentroid\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mm\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m      4\u001b[0m     \u001b[1;32mreturn\u001b[0m \u001b[0mtuple\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mcentermost_point\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m      5\u001b[0m \u001b[0mcentermost_points\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mclusters\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mmap\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mget_centermost_point\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n",
      "\u001b[1;32m~\\Anaconda3\\lib\\site-packages\\shapely\\geometry\\point.py\u001b[0m in \u001b[0;36mx\u001b[1;34m(self)\u001b[0m\n\u001b[0;32m     54\u001b[0m     \u001b[1;32mdef\u001b[0m \u001b[0mx\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mself\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m:\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m     55\u001b[0m         \u001b[1;34m\"\"\"Return x coordinate.\"\"\"\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m---> 56\u001b[1;33m         \u001b[1;32mreturn\u001b[0m \u001b[0mself\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mcoords\u001b[0m\u001b[1;33m[\u001b[0m\u001b[1;36m0\u001b[0m\u001b[1;33m]\u001b[0m\u001b[1;33m[\u001b[0m\u001b[1;36m0\u001b[0m\u001b[1;33m]\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m\u001b[0;32m     57\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m     58\u001b[0m     \u001b[1;33m@\u001b[0m\u001b[0mproperty\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n",
      "\u001b[1;31mIndexError\u001b[0m: list index out of range"
     ]
    }
   ],
   "source": [
    "def get_centermost_point(cluster):\n",
    "    centroid = (MultiPoint(cluster).centroid.x, MultiPoint(cluster).centroid.y)\n",
    "    centermost_point = min(cluster, key=lambda point: great_circle(point, centroid).m)\n",
    "    return tuple(centermost_point)\n",
    "centermost_points = clusters.map(get_centermost_point)\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "lats, lons = zip(*centermost_points)\n",
    "rep_points = pd.DataFrame({'LON':lons, 'LAT':lats})\n",
    "rep_points"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "rs = rep_points.apply(lambda row: df[(df['LAT']==row['LAT']) & (df['LON']==row['LON'])].iloc[0], axis=1)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "fig, ax = plt.subplots(figsize=[10, 6])\n",
    "rs_scatter = ax.scatter(rs['LON'], rs['LAT'], c='#99cc99', edgecolor='None', alpha=0.7, s=120)\n",
    "df_scatter = ax.scatter(df['LON'], df['LAT'], c='k', alpha=0.9, s=3)\n",
    "ax.set_title('Full data set vs DBSCAN reduced set')\n",
    "ax.set_xlabel('Longitude')\n",
    "ax.set_ylabel('Latitude')\n",
    "ax.legend([df_scatter, rs_scatter], ['Full set', 'Reduced set'], loc='upper right')\n",
    "plt.show()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "dbscan_silhouette = silhouette_score(X[X.columns[1:3]], db.labels_)\n",
    "dbscan_silhouette"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "dbscan_calinski_harabasz_score = calinski_harabasz_score(X[X.columns[1:3]], db.labels_)\n",
    "dbscan_calinski_harabasz_score\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "dbscan_davies_bouldin_score = davies_bouldin_score(X[X.columns[1:3]], db.labels_)\n",
    "\n",
    "dbscan_davies_bouldin_score"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {},
   "outputs": [],
   "source": [
    "import numpy as np\n",
    "import pandas as pd\n",
    "from sklearn.cluster import MeanShift\n",
    "\n",
    "from matplotlib import pyplot as plt\n",
    "from mpl_toolkits.mplot3d import Axes3D\n",
    "\n",
    "from sklearn.preprocessing import StandardScaler # data normalization\n",
    "from sklearn.metrics import davies_bouldin_score, calinski_harabasz_score, silhouette_score"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "MeanShift()"
      ]
     },
     "execution_count": 10,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ms = MeanShift()\n",
    "ms.fit(X[X.columns[1:3]])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "array([[28.62670634, 77.21780121],\n",
       "       [28.56453641, 77.22072151],\n",
       "       [28.53662674, 77.20900407],\n",
       "       [28.59145472, 77.23144157],\n",
       "       [28.71377913, 77.22334942],\n",
       "       [28.45607614, 77.18491362],\n",
       "       [28.47462477, 77.28708814],\n",
       "       [28.94481722, 77.21872258],\n",
       "       [28.9515616 , 77.2749666 ]])"
      ]
     },
     "execution_count": 11,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ms.cluster_centers_\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 28,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0.49680494481655024"
      ]
     },
     "execution_count": 28,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "meanshift_silhouette = silhouette_score(X[X.columns[1:3]], ms.labels_)\n",
    "meanshift_silhouette"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 29,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "19879.727636162843"
      ]
     },
     "execution_count": 29,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ms_calinski_harabasz_score = calinski_harabasz_score(X[X.columns[1:3]], ms.labels_)\n",
    "ms_calinski_harabasz_score"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 30,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0.6544927241980759"
      ]
     },
     "execution_count": 30,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "ms_davies_bouldin_score = davies_bouldin_score(X[X.columns[1:3]], ms.labels_)\n",
    "\n",
    "ms_davies_bouldin_score"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 59,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "fig = plt.figure()\n",
    "ax = fig.add_subplot(111)\n",
    "ax.scatter(X[X.columns[1:2]], X[X.columns[2:3]], c='k', alpha=0.9, s=3)\n",
    "ax.scatter(y[:,0], y[:,1],  c='#99cc99', edgecolor='r', alpha=0.7, s=120)\n",
    "plt.show()\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
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
   "version": "3.7.4"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
