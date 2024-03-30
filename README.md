# AI-powered-Adaptive-Traffic-Control
利用机器学习和实时交通数据优化交通信号灯的时间，减少拥堵并提高通勤效率。
import random
import time

class TrafficIntersection:
    def __init__(self):
        # Initial traffic light timing (in seconds)
        self.north_south_green_time = 30
        self.east_west_green_time = 30
    
    def simulate_traffic_flow(self):
        # Simulate random traffic flow (vehicles per minute)
        north_south_flow = random.randint(10, 50)
        east_west_flow = random.randint(10, 50)
        return north_south_flow, east_west_flow

    def adjust_traffic_light_timing(self, north_south_flow, east_west_flow):
        # Adjust traffic light timing based on traffic flow
        total_flow = north_south_flow + east_west_flow
        self.north_south_green_time = max(20, 60 * (north_south_flow / total_flow))
        self.east_west_green_time = max(20, 60 * (east_west_flow / total_flow))
    
    def run_simulation(self):
        for _ in range(10):  # Simulate for 10 cycles
            ns_flow, ew_flow = self.simulate_traffic_flow()
            self.adjust_traffic_light_timing(ns_flow, ew_flow)
            print(f"North-South Flow: {ns_flow} vehicles, Green Light Time: {self.north_south_green_time:.2f} seconds")
            print(f"East-West Flow: {ew_flow} vehicles, Green Light Time: {self.east_west_green_time:.2f} seconds")
            time.sleep(1)  # Simulate time delay

if __name__ == "__main__":
    traffic_system = TrafficIntersection()
    traffic_system.run_simulation()
