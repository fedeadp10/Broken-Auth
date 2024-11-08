# Broken-Auth

import requests

def test_session_fixation(url):
    # Crear una sesión y obtener una ID de sesión
    session = requests.Session()
    response = session.get(url)
    initial_session_id = session.cookies.get('session_id')
    
    # Realizar el inicio de sesión (reemplazar con el proceso de inicio de sesión real)
    login_data = {'username': 'testuser', 'password': 'testpass'}
    response = session.post(url + '/login', data=login_data)
    
    # Comprobar si la ID de sesión cambió después del inicio de sesión
    post_login_session_id = session.cookies.get('session_id')
    
    if initial_session_id == post_login_session_id:
        print("¡Posible vulnerabilidad de fijación de sesión detectada!")
    else:
        print("La ID de sesión cambió después del inicio de sesión. Se observó buena práctica.")

# Uso
test_session_fixation('https://example.com')
