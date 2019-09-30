# cristina
def PLS(X, y):
  X = X.copy()
  y = y.copy()
  
  n, p = X.shape
  y_fit = y.mean() * np.ones(n)
  Z = np.zeros_like(X)
  theta = np.zeros(p)
  
  for m in range(p):
    for j in range(p):
    phi = np.dot(X[:, j], y)
  Z[:, m] += phi * X[:, j]
  
  theta[m] = np.dot(Z[:, m], y) / np.dot(Z[:, m], Z[:, m])
  y_fit += theta[m] * Z[:, m]
  
  for j in range(p):
    X[:, j] -= np.dot(Z[:, m], X[:, j]) / np.dot(Z[:, m], Z[:, m]) * Z[:, m]
  return y_fit
